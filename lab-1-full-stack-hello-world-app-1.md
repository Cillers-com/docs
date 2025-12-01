---
description: >-
  Using Bluetext to make a full stack app by incrementally adding, and
  integrating services like Couchbase, a FastAPI, and Temporal.
---

# Lab 1: Full-Stack Hello World App

## Frontend

Run the quick setup before proceeding from the Bluetext Extension before proceeding. Then run the **add-frontend** tool from the Bluetext Extension. You can then prompt the agent with the following.&#x20;

{% code overflow="wrap" %}
```
I have a containerised frontend running through Polytope, modify the code to have a smiley face with a text box underneath it that says "hello from the frontend".
```
{% endcode %}

## API&#x20;

Run the **add-api** tool to from the Bluetext Extension. Then, prompt your agent with the following:

{% code overflow="wrap" %}
```
list the services to see where what is being hosted. Edit the API to hold a hello from the API message with the following endpoints
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

## Couchbase

We can create a collection in Couchbase to store another message. This requires us to call multiple tools&#x20;

1. **add-couchbase** (creates the code to run the couchbase server and the config-manager, and runs both)
2. **add-couchbase-client** (adds client library to the API project)
3. **add-couchbase-models** (scaffolds new couchbase models with CRUD operations and prepares the API to interact with the database). Now we can use those models to write routes that can populate the couchbase collection. The tool requires parameters, which you can name: **messages.**

**Note**: some tools are added to the list of tools dynamically, for example **add-couchbase-client** adds **add-couchbase-models** to the list of available tools. To view these new tools, press refresh in the MCP tools section of the wizard.

We can then prompt the coding agent with the following:

{% code overflow="wrap" %}
```
Couchbase is running and configured in my app in Polytope. Add a message in main.default.messages to hold a hello from couchbase message. change the frontend to add this message underneath.
```
{% endcode %}

When this is done, you can navigate to the couchbase UI. The adress can be found in the services section in Polytope. To log in, use the credentials **user** and **password**\
\
When this is done you can navigate to the couchbase.yml, make a change, and check the couchbase UI.

## Temporal&#x20;

We will now add temporal to manage workflows in our app.&#x20;

{% code overflow="wrap" %}
```
Add Temporal for managing the state of the messages. Create a workflow that starts when the base route of the frontend is visited by the user and ends when the final message is loaded. each message should be an activity within the workflow
```
{% endcode %}

We can now open the temporal UI, the same way we did for couchbase, and look at the workflow that starts each time you refresh the frontend.
