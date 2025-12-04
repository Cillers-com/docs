---
description: >-
  In this lab we will create a full-stack loyalty points system that tracks
  customer orders, manages returns, and awards points for purchases not returned
  in a specific time frame
---

# Lab 2: Loyalty Points System

## 1. Setup

Before proceeding, make sure you are sitting in a new, empty directory, which we will create our project in. Then, open the Bluetext extension from the activity bar on the left. You will have the option to preform a quick setup which configures your workspace for working with Bluetext and Polytope. Run this quick setup and make sure to select "Cline (Recommended)" when asked which coding agent you want to configure.&#x20;

Now, a polytope.yml file has been created at the root of your directory which exposes polytope to bluetext's tools, and Cline has been configured to connect to Polytopes MCP server

## 2. Setting up Core Services

This time, we are going to add all of the services needed for creating our app - we will leave temporal out for now. Lets add the following tools

* add-api (scaffolds and runs FastAPI)
* add-couchbase (starts the couchbase server)
* add-couchbase client (Adds Couchbase client library with all interaction functions)
* add-couchbase-model (one for **order**, and one for **customer**) (this creates a new python file with a template in which we can define our data fields
* add-frontend (adds a React Frontend Template to our project)

Note: some tools are dynamically added to the list of available tools, so make sure to refresh the MCP tools list at the top of the Bluetext extension to see which tools are newly availably.

## 3. Adding fields to our models

Couchbase collections get added once we run the **add-couchbase-model** tool, and now we will add fields in our model files to define their respective attributes. When we add fields to our models, we are defining the schema and validation rules for our data. This ensures that any data entering our system is automatically checked for the correct types (like strings or integers) and is properly formatted before being stored in the database."&#x20;

in api/modules/src/couchbase/models, you will see two different files: **order.py** and **customer.py.** Add the following fields to these files:

**customer.py:**

```python
class CustomerModel(CouchbaseModel):
    [...]
    id: UUID # Primary key - required
    loyalty_points: int
```

**order.py:**

```python
import datetime from datetime

class OrderModel(CouchbaseModel):
    [...]
    id: UUID # Primary key - required
    customer_id: UUID
    created_at: datetime
    returned_at: datetime | None = None # Not set if not returned:
```

We define these attributes so our application knows exactly what data to expect and how to store it in Couchbase. This allows us to reliably save, retrieve, and manipulate records of customers and orders throughout our system.

## 4. Configuring the API

Before we start to prompt, lets make sure Polytope is connected to Cline by selecting "Manage MCP servers"  at the bottom of the Cline UI as shown below.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/Screenshot 2025-12-01 at 14.07.00.png" alt="" width="563"><figcaption></figcaption></figure></div>

Lets create some endpoints to handle the interactions we want to support in our app. Note, we are including a short 30 second time-frame for demo purposes, which simulates the longer, typically 30 day return policies. You can then prompt the agent with the following:&#x20;

{% code overflow="wrap" %}
```
I am running a full stack app template in Polytope, which you can interact with through mcp tools. Build out the API for a simple loyalty points system where customers earn points for purchases they don't return within a specified time window (30 secs). At /modules/api/src/backend/couchbase/models/ I created models for orders and customers. Create REST endpoints for these resources. Allow filtering order by customer, return state, returned after x days. In addition create:

POST orders/{order_id}/return – mark an order as returned by entering now() into returned_at

I have defined the fields and do not make changes to them
```
{% endcode %}

## 5. Frontend

Lets make changes to our frontend. We already have it up and running, and can prompt the agent with the following:

{% code overflow="wrap" %}
```
I want my frontend to feature an order button on the right, and an order history on the left, with the number of loyalty points on the top. Once the user places an order, the list should show their previous orders in chronological order with a "cancel order" option there. Each order should make the loyalty points increase if 30 seconds have passed since the order, if canceleld, then they shouldnt go up. Everything should take place on home.tsx, on the same screen. Regarding the customer, execute a curl command so we can be logged in as a default customer.
```
{% endcode %}

The reason we asked it to run the CURL command is so that we do not have to create logic for creating an account on the frontend, but can still showcase the apps features.

Great! now lets add temporal to our project

## Temporal

We will now add Temporal to our project. Temporal ensures the workflow is reliably timed and can be retried or signaled independently of API calls.&#x20;

run the temporal tools:

* add-temporal (runs the Temporal server)
* add-temporal-client (adds the temporal client library with all interaction functions)
* add-temporal-model (name it pointstracker)(this creates our workflow file)

we can prompt the agent like so:

{% code overflow="wrap" %}
```
We have added a workflow called pointstracker.py. The workflow should start when an order is placed then sleep for 30 seconds (representing the return window). If a return happens within those 30 seconds, a signal should wake the workflow, cancel the pending points, and exit. If no return signal is received before the sleep finishes, the workflow should complete and give the points. The worker is listening on the main-task-queue, so make sure to use that.
```
{% endcode %}

Now, lets head over to the Temporal UI - you can check where its being hosted from the 'services' section of the Polytope UI. You should see a temporal workflow that sleeps for 30 seconds, and if the item is not returned after that, the workflow completes and gives users their points. You should see something like this when an order is placed and not returned in the 30 second window:

<figure><img src="../.gitbook/assets/Screenshot 2025-12-03 at 14.35.54.png" alt=""><figcaption></figcaption></figure>

## Experiment from here!

if you completed the lab, here are some ideas where you could take the app from here!

### 1. Add steps to Ordering process

Currently, our workflow ends abruptly after the return window closes, but real customer interactions continue long after delivery. You can modify the workflow to remain active and wait for user feedback. You can implement a "Leave Review" button on the frontend that only appears after the 30-second timer expires, and create a new API endpoint that transmits this feedback as a Signal to the waiting workflow. This exercise demonstrates how Temporal workflows can pause indefinitely to synchronize with human actions, allowing you to model the entire lifecycle of an order—from purchase to return period to final feedback—within a single, cohesive process.

### 2. Populate the store with Items

Right now, users can only place generic orders, but a real store needs inventory. You can populate your store with some clothing items. You can choose the "quick" path by hardcoding the item details directly into your frontend, or the "full-stack" path by importing a JSON dataset into Couchbase. If you choose the latter, you'll create a new Product model—carefully ensuring the fields you define exactly match the keys in your JSON file—and then upload the data via the Couchbase UI. Create new API endpoints to fetch and serve these items to your application

Your Virtual Machine comes pre-installed with a dataset called clothing\_dataset\_100.json. If you do not want to upload it through the couchbase UI, you can try an alternative approach. To copy the file to the root directory of the running Docker container named "couchbase-couchbase", try the following command:&#x20;

```
docker cp clothing_dataset_100.json $(docker ps -qf name=couchbase-couchbase):/
```

then, run this to import it into Couchbase

```
container: 
couchbase
exec
cbimport json \
  --format list \
  --dataset file:///clothing_dataset_100.json \
  --cluster localhost \
  --username user \
  --password password \
  --bucket main \
  --scope-collection-exp _default.products \
  --generate-key %product_id% \
  --ignore-fields variants
```
