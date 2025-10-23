---
description: >-
  A Step-by-step guide to set up Polytope with Bluetext, run the MCP server, and
  connect coding agents like Claude Code and Cline.
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

Bluetext is a repository of predefined MCP tools, and these tools are made available to Polytope through the inclusion of the Bluetext repository in this file. We can now run the MCP server to use Bluetext with your preferred coding agent. The agent will use these tools to perform development tasks or generate application components.

### 2. Running the MCP

To start the server, run the following command in your terminal:

```bash
pt run --mcp
```

This command locates the highest-level polytope.yml file in your filesystem or git repository. This file becomes the main Polytope configuration that defines which tools are available.&#x20;

### 3. Connecting the MCP to an Agent

Connecting your coding agent to the MCP server allows the agent to access Polytope’s tools directly during development. You can connect the MCP server to any coding agent that supports custom MCP server configuration. Based on our testing, Claude Code and Cline work particularly well. This section outlines the setup process for both, allowing you to use your preferred agent.

**Setup for Claude Code**

To connect Claude Code to your MCP, run the following command:&#x20;

```
claude mcp add polytope-mcp http://localhost:31338/mcp
```

**Setup for Cline**

To connect Cline to the MCP server, configure your cline\_mcp\_settings as follows:

```
{
  "mcpServers": {
    "polytope": {
      "type": "streamableHttp",
      "url": "http://localhost:31338/mcp",
      "alwaysAllow": ["tool3"],
      "disabled": false
    }
  }
}
```

To navigate to this file from the Cline chat interface, select "MCP Servers" from the top, then navigate to the "Configure" tab, and from the bottom select "Configure MCP Servers".&#x20;

### 4. Flight Check

Before you start prompting, there are a few checks you can do to test that the Polytope and the Bluetext repository are set up correctly. First, to see if your agent is connected to the polytope MCP server, you can simply ask your coding agent: "do you have access to the Polytope MCP server?".&#x20;

After this, you can ask "which Bluetext tools are available to you?" if you see tools like add-api, add-frontend etc, bluetext is successfully configured! if you only see tools like describe-container and describe-job, you have not configured the bluetext repo in the polytope.yml file correctly.

### 5. Prompting

Once you have your Polytope MCP running, and you have ensured your agent is connected to the MCP server, you can start to tell your agent what to create! Once you have prompted your agent, it will ask you to approve tool calls that look similar to the following:&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-10-23 at 10.51.31.png" alt=""><figcaption></figcaption></figure>

Once you start approving these tool calls, you will see that the Polytope UI gets populated with containers, services, volumes, and more. While previously empty, the Polytope interface should now look something like this:

<figure><img src="../.gitbook/assets/Screenshot 2025-10-23 at 11.00.38.png" alt=""><figcaption></figcaption></figure>

If you have started creating a project and close the Polytope MCP server (ctrl + C), or if your IDE crashes, you can re-open your project with the following command:

{% code overflow="wrap" %}
```markup
pt run default --mcp
```
{% endcode %}

## 6. Incorrect Configuration

If Polytope and Bluetext are not set up correctly, your configuration or output files will look different from the expected structure. The examples below illustrate common signs of incorrect setup, so you can quickly identify and fix any issues before proceeding.

An indicator that there is an issue either with the Polytope setup or Bluetext repository file is that cline will start to generate code, but the polytope UI will remain empty.&#x20;

A valid setup includes a **modules** folder. If your project appears without it, Polytope and/or Bluetext are not configured correctly. The image below demonstrates the expected project structure when the setup is successful.

<div data-full-width="true"><figure><img src="../.gitbook/assets/Screenshot 2025-10-23 at 12.57.33.png" alt="" width="563"><figcaption></figcaption></figure></div>



An example of the file structure resulting from an incorrect configuration may look similar to the following:&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-10-23 at 13.25.32.png" alt=""><figcaption></figcaption></figure>



Most of the time, scripts will not be executed when using Bluetext. If Bluetext is configured correctly, the coding agent will primarily use tool calls to interact with the running application. If it is not configured correctly, you might see the coding agent attempt to execute commands directly on your machine. The only commands you should see running locally are curl commands.

The sole purpose of running curl commands directly on your machine is to test whether your services are reachable from outside the containers.

