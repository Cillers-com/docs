# Full-Stack Travel App With Temporal

## Full-Stack Travel App With Temporal

Prompts for creating a full-stack travel webapp with Temporal to manage state. This app uses an API, a database, and Temporal workflows to let users plan and complete trips to different cities. The API handles data requests, the database stores cities and trip plans, and Temporal manages the workflow from planning a trip to marking it finished.

#### 1. Build FastAPI <a href="#id-2.-database" id="id-2.-database"></a>

Using this prompt, we can generate the API that provides endpoints to list cities, get details for a specific city, create and view travel plans, and mark a trip as completed.

{% code overflow="wrap" %}
```markup
Build a FastAPI backend for a Nordic cities travel planner. Define two Pydantic models:

- *City*: name (str), greeting (str).
- *Plan*: id (str), city (str), visited (bool), created\_at (datetime).

Implement the core API endpoints for *Plans* using an in-memory list or dictionary for persistence initially:

- POST /plans - Create a travel plan (takes city name, returns plan with generated ID).
- GET /plans - List all travel plans.
- text{POST /plans/\{id\}/visited - Mark a plan as visited.

Also, create a placeholder endpoint for cities: GET /cities (returns a hardcoded list of Stockholm, Copenhagen, Helsinki, and Oslo, each with a brief greeting).
```
{% endcode %}

#### 2. Couchbase <a href="#id-1.-api" id="id-1.-api"></a>

Using this prompt, you can set up a Couchbase server and create a collection to store the city and plan data. This setup allows the API to read and update city and plan information directly from Couchbase instead of keeping it only in memory.

{% code overflow="wrap" %}
```
Connect the existing FastAPI backend to a Couchbase database. 

1. *Couchbase Setup*: Create two collections: main.\_default.cities and main.\_default.plans.
2. *Seeding*: Seed the main.\_default.cities collection with the 4 Nordic cities (Stockholm, Copenhagen, Helsinki, Oslo) and their greetings through the API.
3. *Refactor Endpoints*: Update the POST, GET, and visited endpoints for /plans to read from and write to the main.\_default.plans collection.
4. *Cities Endpoint*: Update GET /cities to read from the newly seeded main.\_default.cities collection.

All modules are already running containerized in Polytope. 
```
{% endcode %}

#### 3. Temporal Workflow <a href="#id-3.-frontend" id="id-3.-frontend"></a>

Let’s create a relatively straightforward Temporal workflow. This workflow will start when the user presses “Plan Trip” on the home page and end when they press “Finished Trip” on the specific trip’s page. By integrating Temporal, we ensure each trip follows a clear, reliable process—from planning to finishing—while allowing the app to handle state and timing automatically in the background.

{% code overflow="wrap" %}
```markup
Add Temporal to the existing FastAPI backend for trip lifecycle management. 

1. *Workflow*: Create a Temporal workflow that accepts the $\text{plan ID}$ and $\text{city}$ as input. It should log the trip start, wait for a signal, and then log the completion.
2. *Integration*: Modify the POST /plans endpoint to start the workflow upon creating a new plan (passing the plan ID and city).
3. *Signal*: Modify the POST /plans/\{id\}/visited endpoint to send a signal to the corresponding running workflow, triggering its completion.

All modules are already running containerized in Polytope.
```
{% endcode %}

#### 4. Frontend <a href="#id-4.-temporal" id="id-4.-temporal"></a>

Let's build a frontend for our web app.&#x20;

{% code overflow="wrap" %}
```
Create a React app that interacts with the completed FastAPI backend. Implement two routes:

- *Home (/): Display city cards (from GET /cities) with their greetings and a "Plan Trip*" button. Clicking the button should call POST /plans and then navigate the user to the Trip Detail view.
- *Trip Detail (/trips/:planId): Show the trip information and a "Mark Trip as Finished*" button. Clicking this should call POST /plans/\{id\}/visited.
```
{% endcode %}

You can now test the frontend by planning and completing one of the trips. If you then open the Temporal UI from the "Services" panel in Polytope, and select one of the workflows, you can see how they are managed. You can see from the completed workflow below that the Temporal workflow started and ended at the points we wanted it to!

<figure><img src="../.gitbook/assets/Screenshot 2025-10-31 at 11.22.41.png" alt=""><figcaption></figcaption></figure>
