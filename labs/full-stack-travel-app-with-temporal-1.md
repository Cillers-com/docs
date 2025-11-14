# Full-Stack Travel App With Temporal

## Full-Stack Travel App With Temporal

Prompts for creating a full-stack travel webapp with Temporal to manage state. This app uses an API, a database, and Temporal workflows to let users plan and complete trips to different cities. The API handles data requests, the database stores cities and trip plans, and Temporal manages the workflow from planning a trip to marking it finished.

#### 1. Couchbase <a href="#id-1.-api" id="id-1.-api"></a>

Using this prompt, you can set up a Couchbase server and create a collection, which will store the city and plan data.&#x20;

{% code overflow="wrap" %}
```
Setup Couchbase for a Nordic cities travel planner. Create two collections: main._default.cities and main._default.plans. 
```
{% endcode %}

#### 2. Build FastAPI <a href="#id-2.-database" id="id-2.-database"></a>

Using these prompts, we can generate the API that provides endpoints to list cities, get details for a specific city, create and view travel plans, and mark a trip as completed.

**Prompt 1:**

{% code overflow="wrap" %}
```
Build a FastAPI backend ready to connect to Couchbase and handle the following resources. 

Cities: name, greeting
Plans: id, city, visited (boolean), created_at
```
{% endcode %}

**Prompt 2:**

{% code overflow="wrap" %}
```
Create these endpoints:

POST /cities - create a new city to visit
GET /cities - list all cities
GET /cities/:city - get specific city
POST /plans - create travel plan (returns plan with id)
GET /plans - list all plans
GET /plans/:id - get specific plan
POST /plans/:id/visited - mark plan as visited

All endpoints should read from and write to the Couchbase collections (main._default.cities and
main._default.plans). Couchbase is already running.
```
{% endcode %}

**Prompt 3:**

{% code overflow="wrap" %}
```
Add data to the app by adding 4 Nordic cities (Stockholm, Copenhagen, Helsinki, Oslo) through curl commands. 
```
{% endcode %}

#### 3. Frontend <a href="#id-4.-temporal" id="id-4.-temporal"></a>

Let's build a frontend for our web app.&#x20;

{% code overflow="wrap" %}
```
Create a React app with two routes:
Home (/): Display city cards with greetings and "Plan Trip" buttons. After planning, show "View Trip & Finish →".
Trip Detail (/trips/:planId): Show trip info and "Mark Trip as Finished" button with back navigation.
The backend is already up and running.
```
{% endcode %}

#### 4. Temporal Workflow <a href="#id-3.-frontend" id="id-3.-frontend"></a>

Let’s create a relatively straightforward Temporal workflow. This workflow will start when the user presses “Plan Trip” on the home page and end when they press “Finished Trip” on the specific trip’s page. By integrating Temporal, we ensure each trip follows a clear, reliable process—from planning to finishing—while allowing the app to handle state and timing automatically in the background.

{% code overflow="wrap" %}
```markup
Add Temporal for trip lifecycle management. Create a workflow that: logs trip start, waits for a
signal, then logs completion. Register all activities with the workflow in workflows/init.py
and pass them to TemporalClient in init/temporal.py. Start the workflow in POST /plans (pass plan ID and city). Signal the workflow in POST /plans/:id/visited to complete it.
The rest of the backend is already up and running.
```
{% endcode %}

You can now test the frontend by planning and completing one of the trips. If you then open the Temporal UI from the "Services" panel in Polytope, and select one of the workflows, you can see how they are managed. You can see from the completed workflow below that the Temporal workflow started and ended at the points we wanted it to!

<figure><img src="../.gitbook/assets/Screenshot 2025-10-31 at 11.22.41.png" alt=""><figcaption></figcaption></figure>
