# Kong AI + API Gateway Hackathon

## Objective

This template is produced to give the participants in the Kong AI + Gateway Hackathon a flying start. This template includes a basic infrastructure configuration, so all they need to do is to integrate with Kong Konnect and Opper AI, before starting to build the functionality that they want to demo.&#x20;

The objective for the hackathon is to explore how to build systems using an AI-powered API Gateway and agents that are specialized to handle different types of requests.

## A Starting Point For Your Demo Project

* The Kong Gateway connected with a complete API (written in Python) with persistent chats stored in Couchbase, a knowledge base, and a full LLM integration through Opper AI.
* A frontend (written in React) that provides a chat interface for users to interact with the API.
* A great container-based dev env on Polytope, including hot reload, that makes it easy to iterate and collaborate on your solution. One command and you and all your team members are up and running with the same environment!

While this is a great starting point, we don't want to do all the work for you, so the implementation is intentionally incomplete. Here are some known issues you'll need to address:

* The bot is very unhelpful!
* The knowledge base is limited and not very useful.
* The bot hallucinates a lot! If it can't find the answer in the knowledge base, it just makes stuff up.

## Installing Your Demo Project

Make sure you have all of the Cillers System Demo Template prerequisites installed:

* [Hardware and Operating System](../hardware-and-operating-system.md)
* [Polytope](../polytope/)&#x20;

Clone the template repo:&#x20;

```bash
git clone https://github.com/Cillers-com/kong-ai-gateway-hackathon.git kong-demo && cd kong-demo
```

Follow the [Kong Konnect integration guide](../integrations/kong-konnect.md).

Follow the [Opper AI integration guide](../integrations/opper-ai.md).&#x20;

## Configure Your Kong Services And Routes

Go to your Kong Konnect Gateway Manager: [https://cloud.konghq.com/us/gateway-manager/](https://cloud.konghq.com/us/gateway-manager/)

### Add The "api" Service

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXevka_0N5nwjrpL3d4QLM80rqnVMdPNl5UdMYacvQyylgZCg9ppgY2ildT7hXLSSp_H5PLaMLMUewKNGKJ8l_CW6lMY4tUWTzk_HePby-qJIn-8Tr-ahNykXz-1WsT755A0TptGpw?key=jC8T-_XneVuC3ZQq8QXN1Z9t" alt=""><figcaption></figcaption></figure>

Click "Gateway Services" in the left sidebar. Click "New gateway service".

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

Specify [http://host.docker.internal:3001](http://host.docker.internal:3002) as Full URL, and "api" as Name. Click “Save”.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Click the “Routes” tab. Click “New route”.&#x20;

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Select Specify “/api”, "/docs", "/redoc" and "/openapi.json" as Paths. Click “View Advanced Fields” and uncheck "Strip Path". Click "Save"&#x20;

### Add The "frontend" Service

Click "Gateway Services". Click "New gateway service".

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

Specify [http://host.docker.internal:3002](http://host.docker.internal:3002) as Full URL, and "frontend" as Name. Click “Save”.

Click the "Routes" tab and then "New route".

&#x20;

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Specify "frontend-route" as Name, "/" as Paths. Click "View Advanced Fields". Uncheck "Strip Path". Click "Save".

Click "Gateway Services". It should now look as follows:&#x20;

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

## Start Your Demo

1. Run the following command in your demo project directory: `pt run stack`
2. Open the UI: [http://localhost:8000](http://localhost:8000)
3. Start building your solution!

## Project Structure

This app has two main components:

* The API - A Python FastAPI backend that handles chat session management, knowledge base querying, and Opper AI integration
* The UI - A React TypeScript frontend that provides the user interface

The API follows a RESTful design with the following endpoints:

* `POST /api/chats` - Create a new chat session
* `GET /api/chats/{chat_id}` - Get a chat session by ID
* `GET /api/chats/{chat_id}/messages` - Get all messages for a chat session
* `POST /api/chats/{chat_id}/messages` - Add a message to a chat session and get a response
* `DELETE /api/chats/{chat_id}` - Delete a chat session and all its messages

Example usage:

```bash
# Create a new chat session
curl -X POST http://localhost:8000/api/chats -H "Content-Type: application/json" -d '{}'

# Get chat details (replace UUID with the one from previous response)
curl http://localhost:8000/api/chats/550e8400-e29b-41d4-a716-446655440000

# Send a message and get a response
curl -X POST http://localhost:8000/api/chats/550e8400-e29b-41d4-a716-446655440000/messages \
  -H "Content-Type: application/json" \
  -d '{"content": "What is your return policy?"}'

# Get chat history
curl http://localhost:8000/api/chats/550e8400-e29b-41d4-a716-446655440000/messages

# Search knowledge base
curl 'http://localhost:8000/api/knowledge-base/search?query=warranty'
```

