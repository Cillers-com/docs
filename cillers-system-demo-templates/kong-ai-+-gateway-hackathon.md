# Kong AI + Gateway Hackathon

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

