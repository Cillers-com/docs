---
description: >-
  Prompts for creating a full-stack hello world app with Temporal to manage
  state.
---

# Full-Stack Hello World Temporal

This app uses an API, a database, and Temporal workflows to let users plan and complete trips to different cities. The API handles data requests, the database stores cities and trip plans, and Temporal manages the workflow from planning a trip to marking it finished.

### 1. API

Using this prompt, we can generate the API that provides endpoints to list cities, get details for a specific city, create and view travel plans, and mark a trip as completed.

{% code overflow="wrap" %}
```
I'm building a demo web app for tracking which cities a person has visited.
As a first step, can you build me an API that has endpoints like:
- GET /cities - lists the available cities
- GET /cities/:city - returns info about a city
- POST /plans - creates a 'plan' to visit a city
- GET /plans - lists plans
- GET /plans/:plan - returns info about a plan
- POST /plans/:plan/visited: marks that the plan was completed (the city was visited)

Each city should have a 'city name' and a 'greeting message'.
Cities:
 Stockholm: "Hello from Stockholm"
 Copenhagen: "Hello from Copenhagen"
 Helsinki: "Hello from Helsinki"
 Oslo: "Hello from Oslo"

Hard-code the city info for now, and store the plans in memory - we'll hook up a 
database and building a UI later.
```
{% endcode %}

### 2. Database

Using this prompt, you can set up a Couchbase server and create a collection to store the city and plan data. This setup allows the API to read and update city and plan information directly from Couchbase instead of keeping it only in memory.

```
Now hook this up to Couchbase. Store both the city and plan data in couchbase.
```

### 3. Frontend

Let's build a frontend for our web app. To keep things simple, we’ll use the following prompt, but feel free to experiment — for example, you could ask your coding agent to design a “futuristic” or “mult-colour” interface.

{% code overflow="wrap" %}
```
Add frontend for our app that displays the message from the 4 cities, with a button below that says plan trip and then a trip finished button appears
```
{% endcode %}

### 4. Temporal

Let’s create a relatively straightforward Temporal workflow. This workflow will start when the user presses “Plan Trip” on the home page and end when they press “Finished Trip” on the specific trip’s page. By integrating Temporal, we ensure each trip follows a clear, reliable process—from planning to finishing—while allowing the app to handle state and timing automatically in the background.

{% code overflow="wrap" %}
```
Integrate Temporal to define a workflow that begins when the user presses “Plan Trip” and ends when they press “Finished Trip”. Plan trip takes place on the home route but finished takes place on the route of the specific app
```
{% endcode %}

Now, if you open the Temporal UI from the "Services" panel in Polytope, and select one of the workflows, you can see how they are managed. You can see from the completed workflow below that the Temporal workflow started and ended at the points we wanted it to!

<figure><img src="../.gitbook/assets/Screenshot 2025-10-31 at 11.22.41.png" alt=""><figcaption></figcaption></figure>
