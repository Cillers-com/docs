---
description: >-
  Applying similar methods as we did in previous lab, we will create a
  full-stack clothing store website which allows us to place orders, with
  workflows managed in temporal
hidden: true
---

# Lab 2: Full Stack Clothing Store

## 1. Setup

Before proceeding, make sure you are sitting in a new, empty directory, which we will create our project in. Then, open the Bluetext extension from the activity bar on the left. You will have the option to preform a quick setup which configures your workspace for working with Bluetext and Polytope. Run this quick setup and make sure to select "Cline (Recommended)" when asked which coding agent you want to configure.&#x20;

Now, a polytope.yml file has been created at the root of your directory which exposes polytope to bluetext's tools, and Cline has been configured to connect to Polytopes MCP server.

## 2. API

First lets add an API. Then, lets add an endpoint that fetches from this to our already established API. Lets add a get endpoint for the following, and ask the agent to fetch the output to our added API:&#x20;

```python
https://fakestoreapi.com/products
```

## 3. Frontend

Lets display this information in the frontend, and add the option to&#x20;
