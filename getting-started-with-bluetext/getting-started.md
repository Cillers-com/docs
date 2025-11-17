---
description: >-
  A Step-by-step guide to set up Polytope with Bluetext, run the MCP server, and
  configure a coding agent of your choice
---

# Getting Started

Make sure to have Polytope installed and set up on your computer. You can find instructions on how to do so here:

* [For macOS users](../polytope/installation-for-macos-users.md)
* [For Windows users](../polytope/installation-for-windows-users.md)
* [For Linux users](../polytope/installation-for-linux-users.md)

### 1. Setup

First, create a new directory for your project. &#x20;

We recommend you initialise the git repository in the project directory. To do so, run the following command in your new directory.

```bash
git init
```

Then, make a polytope.yml file inside it that contains the following:

```yaml
include:
  - repo: gh:bluetext-io/bluetext
```

The Bluetext tools are made available to Polytope through the inclusion of the Bluetext repository in this file. We can now run the MCP server to use Bluetext with your preferred coding agent. The agent will use these tools to perform development tasks or generate application components.

### 2. Running the MCP

To start the server, run the following command in your terminal:

```bash
pt run --mcp
```

This command locates the highest-level polytope.yml file in your filesystem or git repository. This file becomes the main Polytope configuration that defines which tools are available.&#x20;

### 3. Connecting the MCP to an Agent

Connecting your coding agent to the MCP server allows the agent to access Polytope’s tools directly during development. You can connect the MCP server to any coding agent that supports custom MCP server configuration. Based on our testing, Claude Code, Cline and Roo work particularly well.&#x20;

You can find the specific configuration information for the following agents on our documentation:

* [Roo](getting-started.md#setup-for-roo)
* [ClaudeCode](getting-started.md#setup-for-claude-code)
* [Copilot](coding-agent-configuration/setup-for-copilot.md)
* [Cline](coding-agent-configuration/setup-for-cline.md)

Before proceeding to the next step, ensure you have configured an agent of your choice. Most coding agents have documentation which explains how to set up custom MCP servers, incase you want to use a different agent.

### 4. Starting to Prompt

Before continuing, you can consult the [flight check](getting-started.md#id-4.-flight-check) document to test if Bluetext, Polytope, and the agent are configured correctly. Once you have your Polytope MCP running, and you have ensured your agent is connected to the MCP server, you can start to tell your agent what to create! Once you have prompted your agent, it will ask you to approve tool calls that look similar to the following:&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-10-23 at 10.51.31.png" alt=""><figcaption></figcaption></figure>

Once you start approving these tool calls, you will see that the Polytope UI gets populated with containers, services, volumes, and more. While previously empty, the Polytope interface should now look something like this:

<figure><img src="../.gitbook/assets/Screenshot 2025-10-23 at 11.00.38.png" alt=""><figcaption></figcaption></figure>

If you have started creating a project and close the Polytope MCP server (ctrl + C), or if your IDE crashes, you can re-open your project with the following command:

{% code overflow="wrap" %}
```markup
pt run default --mcp
```
{% endcode %}

If you suspect Bluetext or Polytope are not configured correctly, you can consult the [troubleshooting](broken-reference) documentation.
