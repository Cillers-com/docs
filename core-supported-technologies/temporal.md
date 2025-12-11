---
description: >-
  In this section we explain Temporal, suggest some practical use cases, and
  walk through how to use Bluetext to quickly set up a Temporal workflow
---

# Temporal

{% hint style="info" %}
## You can download the repository which demonstrates Temporal workflows, activities, and other Temporal features from here

[https://github.com/bluetext-io/Temporal-Workflow-Demo](https://github.com/bluetext-io/Temporal-Workflow-Demo)
{% endhint %}

{% hint style="info" %}
## **You can watch the video that explains Temporal's key concepts and demonstrates how you can add a workflow to your Bluetext projects from here**

[https://youtu.be/nd3wVMt4NzU](https://youtu.be/nd3wVMt4NzU)
{% endhint %}

## 1. What is Temporal

Temporal is an open-source workflow orchestration tool which can be used to build long-running, fault-tolerant apps. Developers write workflow steps in normal programming languages, and Temporal guarantees that these steps will eventually complete, even if servers crash, deploy, fail, or lose connectivity. Temporal records workflow execution history as events and can replay code to exactly restore state.&#x20;

## 2. Why Temporal?

Instead of forcing developers to manage retries, state persistence, timeouts, queues, and complex failure recovery logic, Temporal allows them to write business logic as clean, deterministic code in the language of their choice, while the platform guarantees that workflows continue exactly where they left off even if a the process restarts, or an external dependency becomes unreachable.  Temporal makes application code more maintainable, testable, and resilient, with built-in visibility through the Web UI, that ensures developers can inspect and debug system state at any time. This combination of reliability, clear code structure, and transparent state, makes Temporal a powerful foundation for building robust distributed applications that scale without adding operational complexity.

## 3. Core Concepts: Workflows, Activities, and Workers

Workflows, Activities, and Workers form the core of Temporal’s execution model. Understanding how they interact is essential for building reliable, scalable applications. This section explains the purpose of each component and how they work together.

### Workflows

Temporal **workflows** describe when things happen and in what order. **Workflows** are generally composed of one or more **activities**, which are the functions that perform the actual side effects such as calling external services, writing to databases, or sending emails. We will discuss activities in more detail in the next section.

A Workflow in Temporal is the deterministic, durable orchestration of your application’s business logic, expressed as normal code that continues running even if servers, workers, or processes fail. Workflows coordinate tasks, call Activities, manage retries, and maintain state through Temporal’s durable execution engine, allowing them to run for minutes or even years. Because workflows must be deterministic, they cannot perform external I/O, generate random values, depend on system time, or import non-deterministic libraries—these operations belong inside Activities. In the Python SDK, workflows are defined using the `@workflow.defn` and `@workflow.run` decorators. Best practices include keeping workflow files small and isolated, focusing workflow code purely on orchestration, and placing all side-effecting logic into Activities to ensure replay safety and long-term maintainability.

<figure><img src="../.gitbook/assets/Screenshot 2025-12-09 at 13.19.29.png" alt=""><figcaption></figcaption></figure>

Above is what a completed workflow looks like in the Temporal UI.&#x20;

#### Developing a basic workflow in Python

Creating workflows starts with the development of a workflow definition. In the Temporal Python SDK programming model, Workflows are defined as classes. Specify the `@workflow.defn` decorator on the Workflow class to identify a Workflow. Use the `@workflow.run` decorator to mark the entry point method to be invoked; this must be an asynchronous method defined within the same class. Run methods accept parameters that must be serializable, with dataclasses recommended for structured inputs.

Within the workflow, you can orchestrate one or more **Activities** — discrete tasks that handle the actual business logic or interactions with external systems. Workflows themselves should remain deterministic, meaning they should always produce the same sequence of operations given the same input.

<details>

<summary>Example workflow in Python</summary>

```python
from temporalio import workflow
from dataclasses import dataclass
from datetime import timedelta

@dataclass
class YourParams:
    greeting: str
    name: str

@workflow.defn(name="YourWorkflow")
class YourWorkflow:
    @workflow.run
    async def run(self, params: YourParams) -> str:
        return await workflow.execute_activity(
            your_activity,
            params,
            start_to_close_timeout=timedelta(seconds=10)
        )
```

</details>

{% hint style="info" %}
**Remember:** Workflow code must be deterministic. This means:

* no threading
* no randomness
* no external calls to processes
* no network I/O
* no global state mutation
* no system date or time
{% endhint %}

### **Activities**

Activities handle non-deterministic, failure-prone tasks in Temporal, such as calling external services, sending emails, or processing data. Unlike Workflows, Activities do not need to be deterministic, but they should be idempotent to safely support retries.&#x20;

By isolating business logic and side effects in Activities, Workflows remain focused on **orchestration**, simple, and fully deterministic, while Temporal ensures **durable execution** and automatic retries when failures occur.

An Activity is a normal function or method that executes a single, well-defined action (either short or long running), such as calling another service, transcoding a media file, or sending an email message. Activity code can be non-deterministic. Temporal reccomends that it be [idempotent](https://docs.temporal.io/activity-definition#idempotency). Keep workflow code focused on orchestration. \
\
Idempotency in activities is a critical requirement because the Temporal Service automatically retries failed Activities due to network issues, Worker crashes, or timeouts. If a non-idempotent Activity fails _after_ completing its side effect but _before_ reporting completion to Temporal, the retry will cause the side effect to happen again. For example, instead of writing an Activity that subtracts $10 from a bank balance (which would subtract $10 on every retry), write one that verifies the final balance is correct or uses a unique transaction ID to ensure the subtraction only happens once on the external system. This guarantee ensures your business logic remains safe and reliable even when failures occur.\
\
The key is to keep Activities focused on a single, well-defined task, while still including enough detail to support observability and troubleshooting.

#### Activity execution and timeouts

When an activity is being executed by the worker, there are three steps involved

1. **Schedule** - When Temporal first records the intention of executing the task
2. **Start** - The moment execution is began by the worker
3. **Close** – The task finishes, either successfully, with an error, or by being timed out. Temporal records this completion in the Workflow’s Execution History.

Below you can see a visualisation of the process of an activity being executed. This specific activity fetches a message from Couchbase and displays it on the frontend

<figure><img src="../.gitbook/assets/Screenshot 2025-12-09 at 14.22.23.png" alt=""><figcaption></figcaption></figure>

In Temporal, **timeouts for Activities** are crucial for ensuring reliability and detecting failures in workflows. There are four different types:

1. **Schedule-To-Start Timeout:** limits how long an Activity Task can sit in a Task Queue before a Worker starts it, helping detect situations where the Worker fleet is unable to keep up.&#x20;
2. **Start-To-Close Timeout:** sets a maximum duration for a single Activity Task execution, allowing Temporal to detect crashes or lost communication and trigger retries if configured.&#x20;
3. **Schedule-To-Close Timeout:** enforces an upper bound on the overall Activity Execution, including all retries, ensuring tasks don’t block a workflow indefinitely.
4. **Activity Heartbeats:** and the corresponding **Heartbeat Timeout** are important for long running tasks. Heartbeats are periodic signals sent by the Worker to indicate that progress is being made, while the Heartbeat Timeout defines the maximum allowed time between these signals. If the timeout is exceeded, the Activity is considered failed and retried according to the Retry Policy.&#x20;

A Temporal Activity Execution must have at least one of the following timeouts configured to prevent an Activity from running indefinitely in the face of various failures:

* **Schedule-To-Close Timeout**
* **Start-To-Close Timeout**

If both are unset, the Activity will fail immediately upon being scheduled unless a default is set by the Activity's type registration.

You can develop an Activity Definition by using the `@activity.defn` decorator. Register the function as an Activity with a custom name through a decorator argument, for example `@activity.defn(name="your_activity")`.

<details>

<summary>Example activity in Python</summary>

```python
from temporalio import activity
# ...
# ...
@activity.defn(name="your_activity")
async def your_activity(input: YourParams) -> str:
    return f"{input.greeting}, {input.name}!"
```

</details>

## Workers and Task Queues

The Worker is the external process responsible for executing your application code (Workflows and Activities). Running outside the Temporal Service, the Worker establishes a persistent connection to the cluster, allowing it to continuously poll for new Tasks. A Task is the data package (context) the Worker needs to advance a specific execution. There are three main types of Tasks: the Workflow Task, which tells the Workflow Worker to advance the orchestration logic and issue new commands; the Activity Task, which instructs the Activity Worker to run the side-effecting business logic; and the Nexus Task, which handles external service interactions. Workers are fundamentally stateless regarding the Workflow Execution itself, as the Temporal Service maintains the history. This stateless nature allows a single Worker to manage a very large number of open Workflow Executions efficiently, as blocked states can be unloaded and resumed on any available Worker.

The Task Queue is the lightweight, dynamically allocated communication channel that connects the Temporal Service to your Workers. Workers poll Task Queues only when they have capacity, which ensures load balancing across the Worker fleet. Task Queues are implicitly created upon first use and are mandatory for both starting a Workflow Execution and running a Worker, ensuring all Tasks are routed correctly. Workflow and Activity Tasks are persisted in the queue for durability, while Nexus and Query Tasks are delivered instantly via sync matching.

Once an Activity task is finished executing, the Worker responds to the Temporal Service with a specific event:&#x20;

* ActivityTaskCanceled
* ActivityTaskCompleted
* ActivityTaskFailed
* ActivityTaskTerminated
* ActivityTaskTimedOut

## Using Temporal with Bluetext

Bluetext integrates Temporal through MCP tools. First, the **add-temporal** tool scaffolds and starts the Temporal server, Postgres backend (which stores Temporal data), and UI as Polytope-managed containers. Second, the **add-temporal-client** tool adds the temporal-client library, creates configuration and initialization hooks, and registers the **add-temporal-workflow** tool in polytope.yml, making it discoverable to AI agents. Third, the **add-temporal-workflow** tool automatically scaffolds complete workflow files with Pydantic models and activities, then registers them for immediate execution. This progressive enhancement enables AI agents and experiened programmers to autonomously build Temporal functionality by first establishing server infrastructure, then client connectivity, and finally discovering workflow creation capabilities.

To demonstrate how Temporal makes the execution of tasks that rely on external services reliable, try creating an application that integrates these dependencies using a Workflow and Activities!&#x20;

We created an example app, which displays messages from different services in chronological order. First, a message from our FastAPI is fetched, then one from Couchbase (database). Then we wait for user intervention to generate two more (one from PokeAPI and one from Offical Dad Joke API. To demonstrate the workflow features we talked about previously, we implemented signallig and sleeping. The following is a screenshot from the app.

The Workflow<br>

* User accesses base route of frontend (refreshes page), and the Workflow Starts.
* Next, the workflow sleeps for **5 seconds**
* Next, the **Couchbase Activity** runs to fetch the message from the database.
* Then, the **Verification Activity** runs to generate a fake inspector name using Faker.
* The workflow then **pauses** and waits for a **Signal** (user clicks the button).
* Once signaled, the workflow executes **Parallel Activities**: fetching a Pokemon name AND a Dad Joke simultaneously.
* Finally, the workflow completes and returns all data to the frontend.

<figure><img src="../.gitbook/assets/Screenshot 2025-12-09 at 13.19.29.png" alt=""><figcaption></figcaption></figure>

