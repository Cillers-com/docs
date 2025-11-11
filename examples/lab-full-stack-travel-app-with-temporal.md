# LAB: Full-Stack Travel App With Temporal

## Full-Stack Travel App With Temporal

Prompts for creating a full-stack travel webapp with Temporal to manage state.This app uses an API, a database, and Temporal workflows to let users plan and complete trips to different cities. The API handles data requests, the database stores cities and trip plans, and Temporal manages the workflow from planning a trip to marking it finished.

#### 1. Couchbase <a href="#id-1.-api" id="id-1.-api"></a>

{% code overflow="wrap" %}
```
Setup Couchbase for a Nordic cities travel planner. Create two collections: main._default.cities and main._default.plans.

Data models:
Cities: name, greeting
Plans: id, city, visited (boolean), created_at

Seed the database with 4 Nordic cities (Stockholm, Copenhagen, Helsinki, Oslo).
```
{% endcode %}

#### 2. Build FastAPI <a href="#id-2.-database" id="id-2.-database"></a>

{% code overflow="wrap" %}
```markup
Build a FastAPI backend connected to Couchbase. Create these endpoints:
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

#### 3. Temporal Workflow <a href="#id-3.-frontend" id="id-3.-frontend"></a>

{% code overflow="wrap" %}
```markup
Add Temporal for trip lifecycle management. Create a workflow that: logs trip start, waits for a
signal, then logs completion. Register all activities with the workflow in workflows/init.py
and pass them to TemporalClient in init/temporal.py. Start the workflow in POST /plans (pass plan ID and city). Signal the workflow in POST /plans/:id/visited to complete it.
The rest of the backend is already up and running.
```
{% endcode %}

#### 4. Frontend <a href="#id-4.-temporal" id="id-4.-temporal"></a>

{% code overflow="wrap" %}
```
Create a React app with two routes:
Home (/): Display city cards with greetings and "Plan Trip" buttons. After planning, show "View Trip & Finish →".
Trip Detail (/trips/:planId): Show trip info and "Mark Trip as Finished" button with back navigation.
The backend is already up and running.
```
{% endcode %}
