---
description: >-
  An example Bluetext workflow to create a simple Hello World webapp with
  Couchbase, API, and frontend
hidden: true
---

# Simple Full-Stack Hello World App

### Overview

This example sets up a simple full-stack web application. The webapp consists of:

**React (with React Router, shadcn/ui components, running with Bun)** – frontend that fetches and displays the message

**FastAPI** – Backend API to retrieve the message

**Couchbase Database** – To store the message

**Temporal** - To manage the state of the message

The system stores "Hello World" in Couchbase, retrieves it via the API, and renders it in the frontend. A Temporal workflow is then added to track the state of the message.

### 1. Setup

Before starting your project, you need to consult the [Getting Started](/broken/pages/zdXVHt54hjr7fcBUJQDF) document, which explains how to install Polytope, initialize your project directory and git repository, configure MCP servers, and connect tools like ClaudeCode and Clein.

### 2. Generating the API with bluetext

To get a good feeling of how to work with bluetext and how the agent handles toolcalls, lets generate the app step by step. To generate the API, you can give Claude a prompt. Here is what we came up with:

{% code overflow="wrap" %}
```markup
Create a FastAPI application with a GET endpoint at /message that returns the JSON: {"message": "Hello from the API"}.
```
{% endcode %}

Once we submit the prompt, Claude asks us if we would like to run the "add api" toolcall. Accept it. now our API will be scaffolded and will start running.

<figure><img src="../.gitbook/assets/Screenshot 2025-09-18 at 10.15.24.png" alt=""><figcaption></figcaption></figure>

Claude then asks us if it can make some changes to the code. We will also accept this and all following requests. Once finished, Claude will let us know the API is ready and on which port it's running. To test if the API is running you can manually curl the API in another terminal.

```bash
curl  http://localhost:32859
```

### 3. Generating the frontend with bluetext

To add a frontend that takes this message from the API and displays it to the user,  give Claude a prompt like this:

{% code overflow="wrap" %}
```
Create a UI to display the message from the backend. Show a "Loading..." state during the request.
```
{% endcode %}

Just like previously with the API, Claude will ask us if its okay to run the "add frontend" toolcall. Once the frontend is scaffolded and running, Claude will let us know when we are ready to test it and where the frontend is served. You can now review the frontend by opening the frontend adress in your browser. Once we open the frontend, we can see the message on the screen.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-09-18 at 10.18.53.png" alt=""><figcaption></figcaption></figure>

### 4. Implementing Couchbase to our webapp

To take our webapp one step further, we will implement Couchbase to store the string instead of it being hard coded in the API. To do this, give Claude a prompt similar to this:

{% code overflow="wrap" %}
```markup
Integrate Couchbase. Modify the API endpoint to fetch and return a "Hello World" message from a Couchbase document.    
```
{% endcode %}

Claude will then ask us to run the add Couchbase toolcall, which will scaffold Couchbase, run it, and run the config manager, which sets up all required Couchbase configurations. Once this is completed, Claude will run some Curl commands to test if its working, and will then let us know that it has fully implemented Couchbase, and that it stores the string, and is successfully retrieved by the API. Therefore, if we make changes to the string in Couchbase, we should see these changes in the frontend!&#x20;

The default adress for the Couchbase ui is:

```
curl  http://localhost:32859
```

We can open up the Couchbase ui, and view the string from the documents section. To edit it, we can click the edit (pencil) button, and change the hello world string to say something else. We will change it to say "Hello Dino".



<figure><img src="../.gitbook/assets/Screenshot 2025-09-18 at 10.48.38.png" alt=""><figcaption></figcaption></figure>

Now, when we go back to our frontend, this change should be reflected in the frontend! The generated app automatically refreshed for us, but you might need to refresh the frontend yourself.&#x20;

### 5. Temporal Integration

We can add **Temporal** to our app to orchestrate and manage the backend workflow more reliably. Our prompt was:&#x20;

{% code overflow="wrap" %}
```markup
Integrate Temporal. Create a workflow and activity to fetch the message from Couchbase. Add a POST /async-message endpoint to start the workflow and GET /async-message/result/{workflow_id} to retrieve the result. Update the UI to use this flow.
```
{% endcode %}

In effect, this introduces Temporal’s workflow orchestration into the stack, making message retrieval more resilient, traceable, and scalable for more complex processes in the future. You can access the UI from the "services" panel in Polytope.
