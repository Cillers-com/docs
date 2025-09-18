---
description: >-
  A Step-by-step guide to set up Polytope with Bluetext, run the MCP server, and
  connect coding agents like Claude Code and Clein.
---

# Setting Up Your Project

### 1. Setup

Make sure to have Polytope installed and setup on your computer. You can find instructions on how to do so here:

* [For macOS users](../polytope/installation-for-macos-users.md)
* [For Windows users](../polytope/installation-for-windows-users.md)
* [For Linux users](../polytope/installation-for-linux-users.md)

first create a new directory for your project, and make a polytope.yml file inside it that contains the following:

```yaml
include:
  - repo: gh:bluetext-io/bluetext
```

Initialise the git repository in the project directory. To do that, you need to be standing in your project directory and run the following command:

```bash
git init
```

This initialises the git repository and informs polytope where the root of the project is. Polytope treats the polytope.yml file at the root as the source from which to discover modules and tools. MCP tools defined by bluetext are available to Polytope through the inclusion of the Bluetext repo in this file.

We can now run the MCP server to use Bluetext with your favourite coding agent. These tools will be used by Claude to create the app. To do this, run the following command in your terminal.&#x20;

```bash
pt run --mcp
```

To connect ClaudeCode to your MCP, run the following command&#x20;

```
claude mcp add polytope-mcp http://localhost:31338/mcp
```

To connect Clein to your MCP, change your clein\_mcp\_settings to say the following

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

