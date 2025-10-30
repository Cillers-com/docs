---
description: >-
  Prompts for creating a full-stack hello world app with Temporal to manage
  state.
---

# Full-Stack Hello World Temporal



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

Hard-code the city info for now, and store the plans in memory - we'll hook up a database and building a UI later.
```

```
Now hook this up to Couchbase. Store both the city and plan data in couchbase.
```

{% code overflow="wrap" %}
```
Add frontend for our app that displays the message from the 4 cities, with a button below that says plan trip and then a trip finished button appears
```
{% endcode %}

{% code overflow="wrap" %}
```
Integrate Temporal to define a workflow that begins when the user presses “Plan Trip” and ends when they press “Finished Trip”. Plan trip takes place on the home route but finished takes place on the route of the specific app
```
{% endcode %}
