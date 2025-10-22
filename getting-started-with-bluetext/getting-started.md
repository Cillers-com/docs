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

First create a new directory for your project. &#x20;

We recommend you Initialise the git repository in the project directory. To do so, run the following command.

```bash
git init
```

Then, make a polytope.yml file inside it that contains the following:

```yaml
include:
  - repo: gh:bluetext-io/bluetext
```

The MCP tools defined by Bluetext are made available to Polytope through the inclusion of the Bluetext repository in this file. We can now run the MCP server to use Bluetext with your preferred coding agent. The agent will use these tools to perform development tasks or generate application components.\


To start the server, run the following command in your terminal:

### 2. Running the MCP

```bash
pt run --mcp
```

This command locates the highest-level polytope.yml file in your filesystem or git repository. This file becomes the main Polytope configuration that defines which tools are available.

### 3. Connecting the MCP to an agent

You can connect the MCP server to any coding agent that supports custom MCP server configuration. Based on our testing, Claude Code and Cline work particularly well. This section outlines the setup process for both, allowing you to use your preferred agent.

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
