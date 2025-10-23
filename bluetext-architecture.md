---
description: >-
  This document covers how Bluetext, Polytope, and coding agents work together
  to improve application development through automated scaffolding, container
  orchestration, and tool-based workflows.
---

# Bluetext Architecture

## **Bluetext**

When generating apps and services, Bluetext functions as a repository of predefined MCP tools and application templates that establish consistent, best-practice project structures. It provides developers with a library of standardized templates for frontends, APIs, and databases, ensuring that every generated project follows a predictable and modular layout. By defining reusable components and scaffolding patterns, Bluetext eliminates repetitive setup work and promotes uniformity across services. It also manages dependencies and configurations, allowing seamless integration with Polytope’s orchestration capabilities.

## Polytope

Polytope serves as an orchestration platform that manages containerization and exposes Bluetext’s tools through its MCP server. When using Bluetext, Polytope acts as the execution layer of the ecosystem, handling service creation, container management, and inter-service communication. When the coding agent requests a Bluetext tool, Polytope interprets the call, scaffolds the necessary templates, and spins up fully configured containers for each service. It ensures all components operate in isolated environments with features such as hot reload and automatic networking.

## The Coding Agent

Any coding agent that supports custom MCP server configuration can be used with Bluetext. The agent communicates with Polytope, issuing specific tool calls to scaffold services, manage containers, and configure infrastructure. The agent also performs all the functions of a standard coding assistant—writing code, implementing business logic, and debugging. This dual functionality allows developers to benefit from automated infrastructure provisioning through Bluetext tools alongside traditional AI-assisted coding.&#x20;

