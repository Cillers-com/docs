# Setup for Copilot

To connect Copilot agent to the MCP, you need to create a .vscode directory at the root of your project. then create an mcp.json file inside this directory, with the following configuration

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

**note**: this setup is slightly different than the other configurations, as this needs to be done for every project before you proceed to start prompting.
