---
description: >-
  In this section we explain Temporal, show practical use cases, and walk
  through Bluetext configuration
---

# Temporal

## 1. Temporal

Temporal is an open-source workflow orchestration tool which can be used to build long-running, fault-tolerant apps. Developers write workflow steps in normal programming languages, and Temporal guarantees that these steps will eventually complete, even if servers crash, deploy, fail, or lose connectivity. Temporal records workflow execution history as events and can replay code to exactly restore state.&#x20;

Temporal **workflows** describe when things happen and in what order. **Workflows** are generally composed of one or more **activities**, which are the functions that perform the actual side effects such as calling external services, writing to databases, or sending emails.&#x20;

In the context of an online clothing store, the ordering **workflow** is the process that coordinates the steps of ordering clothes, while the **activities** are the individual steps that make up the **workflow,** for example charging the payment, and sending the confirmation email.

The example below shows an example workflow for a clothes ordering workflow in the Temporal UI, from placing the order, to paying and writing your email for confirmation.

<figure><img src="../.gitbook/assets/Screenshot 2025-11-04 at 15.29.44.png" alt=""><figcaption></figcaption></figure>

## **2. Temporal in Bluetext**

Bluetext integrates Temporal through a three-phase tool discovery system. First, add-temporal scaffolds and starts the Temporal server, Postgres backend (which stores Temporal data), and UI as Polytope-managed containers. Second, add-temporal-client adds the temporal-client library, creates configuration and initialization hooks, and registers the -add-temporal-workflow tool in polytope.yml, making it discoverable to AI agents. Third, when agents call the workflow tool, it automatically scaffolds complete workflow files with Pydantic models and activities, then registers them for immediate execution. This progressive enhancement enables AI agents to autonomously build Temporal functionality by first establishing server infrastructure, then client connectivity, and finally discovering workflow creation capabilities.
