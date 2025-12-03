---
description: >-
  Using Bluetext to make a full stack app by incrementally adding services like
  Couchbase, a FastAPI, and Temporal.
---

# Lab 1: Full-Stack Hello World App

## 1. Setup

Before proceeding, make sure you are sitting in a new, empty directory, which we will create our project in. Then, open the Bluetext extension from the activity bar on the left. You will have the option to preform a quick setup which configures your workspace for working with Bluetext and Polytope. Run this quick setup and make sure to select "Cline (Recommended)" when asked which coding agent you want to configure.&#x20;

Now, a polytope.yml file has been created at the root of your directory which exposes polytope to bluetext's tools, and Cline has been configured to connect to Polytopes MCP server.

## 2. Frontend

First, we are going to create a frontend that displays a message with a smiley face.

After starting the MCP server from the Bluetext extension, run the **add-frontend** tool. Then, open up Cline and ensure it is connected to polytope by selecting "Manage MCP servers"  at the bottom of the Cline UI as shown below.



<div data-with-frame="true"><figure><img src=".gitbook/assets/Screenshot 2025-12-01 at 14.07.00.png" alt="" width="563"><figcaption></figcaption></figure></div>

You can then prompt the agent with the following:&#x20;

{% code overflow="wrap" %}
```
I have a containerised frontend running through Polytope, modify the code to have a smiley face with a text box underneath it that says "hello from the frontend".
```
{% endcode %}

After Cline tells us that its finished making these changes, we can inspect the frontend ourselves.

Our frontend is served on our local network through polytope - You can navigate to the services section of the Polytope UI to see where certain services are hosted. By default, the frontend will always be hosted at https://localhost:51732&#x20;

Great, now you can see the frontend with the hello world message with a smiley face!

## 3. API&#x20;

Next we are going to add an api that has a hardcoded message that says "hello from the API" which gets posted onto the frontend in a separate text box.

First, run the **add-api** tool from the Bluetext Extension. Then, prompt your agent with the following:

{% code overflow="wrap" %}
```
list the services to see where what is being hosted. Edit the API to hold a hello from the API message with the following endpoints:
GET  /message: returns the hardcoded message
POST /message: replaces the hardcoded message (optional) 

Edit the frontend to display this message under the existing one
```
{% endcode %}

we can check the API directly either by visiting this endpoint trough the browser, or by curling the endpoint.&#x20;

Your agent might ask you to approve a CURL request that would look like the following:&#x20;

```
curl -X POST "http://localhost:3030/message?message=your+new+message"
```

Next, visit the frontend to check if this second message gets displayed.

## 4. Couchbase

We are going to use Couchbase to persistently store a message that says "hello from Couchbase" which will get displayed onto the frontend in a third text box

With Bluetext, This requires us to call multiple tools&#x20;

1. **add-couchbase** (creates the code to run the Couchbase server and the config-manager, and runs both)
2. **add-couchbase-client** (adds client library to the API project)
3. **add-couchbase-models** (scaffolds new couchbase models with CRUD operations and prepares the API to interact with the database). Now we can use those models to write routes that can populate the couchbase collection. The tool requires parameters, which you can name: **messages.**

**Note**: some tools are added to the list of tools dynamically, for example **add-couchbase-client** adds **add-couchbase-models** to the list of available tools. To view these new tools, press refresh in the MCP tools section of the wizard.

in modules/\<api-name>-api/src/couchbase/models/messages.py, import the datetime module at the top of the file together with the other built in module imports.&#x20;

```python
from datetime import datetime
```

Then add the following fields to the messages class at the bottom of the file:

```python
class MessagesModel(CouchbaseModel):
    [...]
    author: str
    created_at: datetime
    message: str
```

We can then prompt the coding agent like so:

{% code overflow="wrap" %}
```
I have a fullstack app up and running through Polytope. You can interact with it using mcp tools.
Implement API REST endpoints for the Messages model to store items in the db. You can find the model at modules/api/src/couchbase/models/messages.py. We will test your endpoints in the next prompt. 
```
{% endcode %}

After the agent is done, use the same context to prompt it to like so:

{% code overflow="wrap" %}
```
Add the following data to the database using the endpoints we just created. 
message: "hello from couchbase" 
author: "couchbase" 
created_at: time of creation (now)
Fetch the message from the API and display it on the frontend in a third textbox
```
{% endcode %}

Congratulations! We successfully set up our API to handle requests for storing data in couchbase and tested it out with our first request.&#x20;

{% hint style="info" %}
Notice how the coding agent made use of `curl` commands. `curl` allows us to make requests to APIs or websites to GET, POST, UPDATE or DELETE data from them.&#x20;
{% endhint %}

You can now navigate to the Couchbase UI to see the changes. In your browser you can navigate to the address specified in the services section of the Polytope UI (https://localhost:8091). You will now be prompted to log in. For development purposes we inject the login credentials as environment variables into the couchbase server set to username: **user** and password: **password.** On the lefthand side you will see the the section `documents` . Click on it and select our `messages` collection in the third dropdown defining our keyspace. You should now see the message we just promped our coding agent to create. We can change this message from within the Couchbase UI to say something else, then go back to our frontend and view the message.

## 5. Temporal

We will now add temporal to manage workflows in our app. Temporal will act as a reliable manager that ensures the multi-step process of fetching messages from different sources is executed correctly.

Just like with Couchbase, 3e will run three different tools from the Bluetext Extension:

* add-temporal
* add-temporal-client
* add-temporal workflow (named messages workflow)

Once the temporal server is running, the client has been added to our project, and we have created the messagesflow.py workflow file, we can prompt Cline with the following.

{% code overflow="wrap" %}
```
I have Temporal up and running and I have create a messagesflow.py workflow file. Create a workflow that starts when the base route of the frontend is visited by the user and ends when the final message is loaded. The process of each message getting displayed should be an activity within the workflow.
```
{% endcode %}

We can now open the temporal UI, the same way we did for couchbase, and look at the workflow that starts each time you refresh the frontend. You should see something like this:

<figure><img src=".gitbook/assets/Screenshot 2025-12-01 at 15.10.33.png" alt=""><figcaption></figcaption></figure>

As shown in the Temporal UI example above, the workflow begins as soon as the frontend’s base route is visited and completes once both the API and Couchbase messages have been retrieved. These activities ran asynchronously, meaning they executed in parallel, though we could just as easily have awaited them to enforce sequential execution.
