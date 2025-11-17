# Setup for Copilot

To connect the Copilot agent to the MCP, you can create a .vscode/ directory at the root of your project. Then create an mcp.json file inside this directory, with the following configuration

```jsonc
{
  "servers": {
    "polytope": {
      "type": "sse",
      "url": "http://localhost:31338/mcp",
      "tools": ["*"]
    }
  }
}
```

Alternatively, you could could configure the MCP globally, so that the MCP server will be available in every project you open in VS Code or Copilot — without needing any per-project configuration.

To do this, open the command palette by pressing **Cmd + Shift + P**, type "MCP: open user configuration", and paste the same configuration shown above there.
