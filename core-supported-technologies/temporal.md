---
description: >-
  In this section we explain Temporal, suggest some practical use cases, and
  walk through how to use Bluetext to quickly set up a Temporal workflow
---

# Temporal

{% hint style="info" %}
## You can download the repository which demonstrates Temporal workflows, activities, and other Temporal features from here


{% endhint %}

## 1. What is Temporal

Temporal is an open-source workflow orchestration tool which can be used to build long-running, fault-tolerant apps. Developers write workflow steps in normal programming languages, and Temporal guarantees that these steps will eventually complete, even if servers crash, deploy, fail, or lose connectivity. Temporal records workflow execution history as events and can replay code to exactly restore state.&#x20;

## 2. Why Temporal?

Instead of forcing developers to manage retries, state persistence, timeouts, queues, and complex failure recovery logic, Temporal allows them to write business logic as clean, deterministic code in the language of their choice, while the platform guarantees that workflows continue exactly where they left off even if a the process restarts, or an external dependency becomes unreachable.  Temporal makes application code more maintainable, testable, and resilient, with built-in visibility through the Web UI, that ensures developers can inspect and debug system state at any time. This combination of reliability, clear code structure, and transparent state makes Temporal a powerful foundation for building robust distributed applications that scale without adding operational complexity.

## 3. Core Concepts: Workflows, Activities, and Workers

Workflows, Activities, and Workers form the core of Temporal’s execution model. Understanding how they interact is essential for building reliable, scalable applications. This section explains what each component does and how they work together.

### Workflows

Temporal **workflows** describe when things happen and in what order. **Workflows** are generally composed of one or more **activities**, which are the functions that perform the actual side effects such as calling external services, writing to databases, or sending emails. We will discuss activities in more detail in the next section.

A Workflow in Temporal is the deterministic, durable orchestration of your application’s business logic, expressed as normal code that continues running even if servers, workers, or processes fail. Workflows coordinate tasks, call Activities, manage retries, and maintain state through Temporal’s durable execution engine, allowing them to run for minutes or even years. Because workflows must be deterministic, they cannot perform external I/O, generate random values, depend on system time, or import non-deterministic libraries—these operations belong inside Activities. In the Python SDK, workflows are defined using the `@workflow.defn` and `@workflow.run` decorators. Best practices include keeping workflow files small and isolated, focusing workflow code purely on orchestration, and placing all side-effecting logic into Activities to ensure replay safety and long-term maintainability.

<figure><img src="../.gitbook/assets/Screenshot 2025-12-09 at 13.19.29.png" alt=""><figcaption></figcaption></figure>

Above is what a completed worlkflow looks like in the Temporal UI.

#### Developing a basic workflow in Python

Creating workflows starts with the development of a workflow definition. In the Temporal Python SDK programming model, Workflows are defined as classes. Specify the `@workflow.defn` decorator on the Workflow class to identify a Workflow. Use the `@workflow.run` decorator to mark the entry point method to be invoked; this must be an asynchronous method defined within the same class. Run methods accept parameters that must be serializable, with dataclasses recommended for structured inputs.

Within the workflow, you can orchestrate one or more **Activities** — discrete tasks that handle the actual business logic or interactions with external systems. Workflows themselves should remain deterministic, meaning they should always produce the same sequence of operations given the same input. Activities are executed asynchronously via `workflow.execute_activity()`, allowing the workflow to progress without blocking on long-running tasks.

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
The key is to keep Activities focused on a single, well-defined task, while still including enough detail to support observability and troubleshooting.

#### Activity execution and timeouts

When an activity is being executed by the worker, there are three steps involved

1. **schedule** - when Temporal first records the intention of executing the task
2. **start** - The moment execution is began by the worker
3. **Close** – The task finishes, either successfully, with an error, or by being timed out. Temporal records this completion in the Workflow’s Execution History.

Below you can see a visualisation of the process of an activity being executed. This specific activity fetches a message from Couchbase and displays it on the frontend

<figure><img src="../.gitbook/assets/Screenshot 2025-12-09 at 14.22.23.png" alt=""><figcaption></figcaption></figure>

In Temporal, **timeouts for Activities** are crucial for ensuring reliability and detecting failures in workflows. There are four different types:

1. **Schedule-To-Start Timeout** limits how long an Activity Task can sit in a Task Queue before a Worker starts it, helping detect situations where the Worker fleet is unable to keep up.&#x20;
2. **Start-To-Close Timeout** sets a maximum duration for a single Activity Task execution, allowing Temporal to detect crashes or lost communication and trigger retries if configured.&#x20;
3. **Schedule-To-Close Timeout** enforces an upper bound on the overall Activity Execution, including all retries, ensuring tasks don’t block a workflow indefinitely.
4. **Activity Heartbeats** and the corresponding **Heartbeat Timeout** are important for long running tasks. Heartbeats are periodic signals sent by the Worker to indicate that progress is being made, while the Heartbeat Timeout defines the maximum allowed time between these signals. If the timeout is exceeded, the Activity is considered failed and retried according to the Retry Policy.&#x20;

A Temporal Activity Execution must have at least one of the following timeouts configured to prevent an Activity from running indefinitely in the face of various failures:

* Schedule-To-Close Timeout
* Start-To-Close Timeout

If both are unset, the Activity will fail immediately upon being scheduled unless a default is set by the Activity's type registration.

Once an Activity task is finished executing, the Worker responds to the Temporal Service with a specific event:&#x20;

* ActivityTaskCanceled
* ActivityTaskCompleted
* ActivityTaskFailed
* ActivityTaskTerminated
* ActivityTaskTimedOut

<details>

<summary>Example activity in Python</summary>

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



**2. Temporal in Bluetext**

Bluetext integrates Temporal through a three-phase tool discovery system. First, **add-temporal** scaffolds and starts the Temporal server, Postgres backend (which stores Temporal data), and UI as Polytope-managed containers. Second, **add-temporal-client** adds the temporal-client library, creates configuration and initialization hooks, and registers the **add-temporal-workflow** tool in polytope.yml, making it discoverable to AI agents. Third, when agents call the workflow tool, it automatically scaffolds complete workflow files with Pydantic models and activities, then registers them for immediate execution. This progressive enhancement enables AI agents to autonomously build Temporal functionality by first establishing server infrastructure, then client connectivity, and finally discovering workflow creation capabilities.

##







