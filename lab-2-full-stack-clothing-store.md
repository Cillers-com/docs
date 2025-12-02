---
description: >-
  Applying similar methods as we did in previous lab, we will create a
  full-stack clothing store website which allows us to place orders, with
  workflows managed in temporal.
hidden: true
---

# Lab 2: Full Stack Clothing Store

## 1. Setup

Before proceeding, make sure you are sitting in a new, empty directory, which we will create our project in. Then, open the Bluetext extension from the activity bar on the left. You will have the option to preform a quick setup which configures your workspace for working with Bluetext and Polytope. Run this quick setup and make sure to select "Cline (Recommended)" when asked which coding agent you want to configure.&#x20;

Now, a polytope.yml file has been created at the root of your directory which exposes polytope to bluetext's tools, and Cline has been configured to connect to Polytopes MCP server.

## 2. Adding API

Lets first create our main API, which will be used for fetching cloting items and information about them from the dataset and displaying them on the frontend, also for creating and cancelling orders. Run the add-api tool, and prompt Cline with the Following. Don't forget to check if Polytope is connected to Cline

{% code overflow="wrap" %}
```python
I have an API running on localhost:3030. Add the following REST API endpoints to it. - - `GET /products` - List all clothing items
- `GET /products/:id` - Get a specific clothing item

- `POST /orders` - Create a new order (Checkout process)
- `GET /orders` - List all orders (can be filtered by user)
- `GET /orders/:id` - Get specific order details
- `POST /orders/:id/cancel` - Cancel an order

```
{% endcode %}

## 3. Couchbase

Run the add-couchbase tool, and the add-couchbase client tool. We can then go into modules/config-manager/conf/couchbase.yml and add our products at the bottom under the default "users" collection like so:&#x20;

```markdown
    scopes:
      _default:
        collections:
          users:
            defaults:  # Per-collection defaults across envs
              max_ttl: 3600
            env_settings:
              staging:
                max_ttl: 7200
              prod:
                max_ttl: 7200
          products: {} ##right here!!
```

Now, if we navigate to the Couchbase UI at localhost:8091, we can see that the collection has been collected. (click on documents on the left)

At the top of the Couchbase UI, you should see an "import" button. On your VM, you will find a clothing\_dataset\_100.json, which we can import from there as a JSON file. also, make sure to select the products collection in your keyspace. Now we can prompt the Agent:&#x20;

{% code overflow="wrap" %}
```
Connect the existing GET /products and GET /products/{id} API routes to the Couchbase products collection. Replace the mock data with actual database queries so the API serves real product data.
```
{% endcode %}

## 4. Frontend

Now that our API and Couchbase collection are ready, we can create the frontend to display clothing items!\
\
in your project directory, run the `add-frontend` tool. Then, tell Cline:&#x20;

{% code overflow="wrap" %}
```
create a frontend interface that fetches clothing items from the API (GET /products) and displays them in a grid layout. 
```
{% endcode %}

we can now also add a cart and checkout funcionality:

<br>

{% code overflow="wrap" %}
```
add the related API endpoints for adding items to a cart, and checking out. Also, make these changes to the frontend too
```
{% endcode %}

