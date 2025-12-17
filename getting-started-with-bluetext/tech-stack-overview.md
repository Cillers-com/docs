# Tech Stack Overview

## Virtual Machines

Our development environment runs on Linux-based virtual machines without a graphical desktop environment.

To make development accessible, we installed **VS Code Server**, which allows you to connect to your VM and develop directly from your browser. You’ll find the access link in the email you received.

We also installed **Chromium** on the VM itself. This browser runs _inside_ the server and is used to view and interact with what you develop locally. Since the application is only accessible from within the server environment, the frontend and service UIs must be viewed through a browser running on the VM. This is why you’ll see a “browser in a browser” setup. You can open Chromium using the link provided in the email.

In addition, the VM comes preinstalled with **Polytope**, **Docker**, and a **coding agent**, all of which are prerequisites for developing with Bluetext. Finally, we installed the **Bluetext Extension**, which streamlines and simplifies the overall Bluetext development experience.

## The Coding Agent

The coding agent acts as an intermediary between you and a Large Language Model (LLM/AI). Its role is to make requests to the model, interpret the responses, and execute development-related actions.

Common tasks performed by the agent include reading and writing code, executing terminal commands, and interacting with the file system. The agent’s capabilities can be extended through **MCP (Model Context Protocol) servers**, which allow additional tools and integrations to be exposed.

## Polytope & MCPs

**Polytope** is responsible for running your application inside containers and orchestrating them. You define what runs and how it runs (for example, your frontend) in configuration files such as `polytope.yml`. In most cases, this setup is handled automatically through Bluetext. You only need to modify these configurations if you want to change container behavior, such as injecting environment variables.

Within Polytope, you can inspect which containers are running, view their logs, and see which services your application exposes and on which ports. Polytope also provides built-in development tools that are exposed to the coding agent, as well as support for custom, self-defined tools.

Bluetext is built on top of this infrastructure. It defines higher-level tools for scaffolding code, running services through Polytope, and supporting day-to-day development workflows

## Bluetext Development Tech Stack

### React Router Frontend

A frontend can be added using the `add-frontend` tool, either manually or via the coding agent. This frontend serves as the main user-facing entry point to the distributed system. It is primarily used for user interaction and for visualizing backend functionality.

The frontend typically triggers requests to API endpoints to fetch or submit data and then displays the results. We use **React** as the frontend framework, with development commonly involving **HTML**, **TypeScript**, and **CSS**.

For routing, we use **React Router 17**, chosen for its predictable and easy-to-understand structure for both humans and AI. The routes you can navigate to are defined under:

```
modules/your-frontend-name/app/routes
```

We also integrate **shadcn/ui** components, so neither you nor the AI needs to build UI components from scratch. These components are easy to customize, and all their source code lives directly in your project under:

```
modules/your-frontend-name/components/ui
```

Instead of installing dependencies manually, you (or the coding agent) should use the `add-dependencies` tool, which installs and validates them automatically.

To view the frontend, open the following URL in your browser:

```
http://localhost:51732
```

### Couchbase

Couchbase can be added using the `add-couchbase` tool. It is an enterprise-ready, feature-complete document database capable of handling millions of requests per second. Couchbase also provides a web-based UI that allows you to manually perform CRUD operations, inspect documents and collections, and monitor performance.

Once Couchbase is added, you can call the `<your-api-name>-add-couchbase-client` tool to programmatically interface with the database from your API.

For development purposes, the Couchbase credentials are:

* **Username:** `user`
* **Password:** `password`

You can access the Couchbase UI at:

```
http://localhost:8091
```

### Couchbase Client

A client library that is added to the project to configure and enable API-level access to Couchbase. The tool can be ran with **api-add-couchbase-client**

### Temporal Client

A client library that is added to the project to configure and enable API-level access to Temporal. The tool can be ran with **api-add-Temporal-client**

### Config Manager

The Config Manager is responsible for configuring Couchbase and other services so they are ready for use. In most cases, it does not require any code changes. You can inspect the configuration it applies to a given service (such as Couchbase) to understand how the service is set up.

### Temporal

**Temporal** is a workflow orchestration and durable task execution platform. It allows you to define business workflows as code, including retry logic and timeouts. These features ensure reliable, fault-tolerant execution of long-running tasks.

### Python FastAPI

