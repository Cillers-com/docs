---
description: >-
  This document covers how Bluetext, Polytope, and coding agents work together
  to improve application development through automated scaffolding, container
  orchestration, and tool-based workflows.
---

# Architecture

<figure><img src=".gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

## Polytope

Polytope serves as an orchestration platform that manages containerization and exposes Bluetext’s tools through its MCP server. When using Bluetext, Polytope acts as the execution layer of the ecosystem, handling service creation, container management, and inter-service communication. When the coding agent requests a Bluetext tool, Polytope interprets the call, scaffolds the necessary templates, and spins up fully configured containers for each service. It ensures all components operate in isolated environments with features such as hot reload and automatic networking.

To learn more about polytope, consult the Polytope documentation: [https://www.polytope.com/docs](https://www.polytope.com/docs)

## **Bluetext**

When generating apps and services, Bluetext functions as a repository of predefined MCP tools and application templates that establish consistent, best-practice project structures. It provides developers with a library of standardized templates for frontends, APIs, and databases, ensuring that every generated project follows a predictable and modular layout. By defining reusable components and scaffolding patterns, Bluetext eliminates repetitive setup work and promotes uniformity across services. It also manages dependencies and configurations, allowing seamless integration with Polytope’s orchestration capabilities.

## The Coding Agent

Any coding agent that supports custom MCP server configuration can be used with Bluetext. The agent communicates with Polytope, issuing specific tool calls to scaffold services, manage containers, and configure infrastructure. The agent also performs all the functions of a standard coding assistant—writing code, implementing business logic, and debugging. This dual functionality allows developers to benefit from automated infrastructure provisioning through Bluetext tools alongside traditional AI-assisted coding.&#x20;

In short, being connected to the Polytope MCP server allows agents both to make use of Polytope's native tools, such as retrieving the logs for error detection, and exposes Bluetext tools to the agent.&#x20;

## Setup Overview

Bluetext runs locally through two simple configuration steps. First, your project directory contains a polytope.yml file that references the Bluetext template repository, giving Polytope access to all scaffolding tools. Second, your coding agent (Claude, Cline, etc.) is configured to connect to the Polytope MCP server running on your machine.&#x20;

For detailed setup instructions for different agents and operating systems, consult the [getting started with bluetext](/broken/pages/7ZDR5ZFkZqMbAhE8Cewp) guide.&#x20;

