---
description: >-
  A Step-by-step guide to set up Polytope with Bluetext, run the MCP server, and
  connect coding agents like Claude Code and Cline.
---

# Getting Started

Make sure to have Polytope installed and setup on your computer. You can find instructions on how to do so here:

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

MCP tools defined by bluetext are available to Polytope through the inclusion of the Bluetext repo in this file. We can now run the MCP server to use Bluetext with your favourite coding agent. These tools will be used by your agent to create the app. To do this, run the following command in your terminal.&#x20;

### 2. Running the MCP

```bash
pt run --mcp
```

This command locates the highest-level polytope.yml file in your filesystem or git repository. This file becomes the main Polytope configuration that defines which tools are available.

### 3. Connecting the agent

To connect Claude Code to your MCP, run the following command:&#x20;

```
claude mcp add polytope-mcp http://localhost:31338/mcp
```

To connect Cline to your MCP, change your cline\_mcp\_settings to say the following

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

