# Setup for Cline

To connect Cline to the MCP server, configure your cline\_mcp\_settings as follows:

```
{
  "mcpServers": {
    "polytope": {
      "type": "streamableHttp",
      "url": "http://localhost:31338/mcp",
      "disabled": false
    }
  }
}
```

To navigate to this file from the Cline chat interface, select "MCP Servers" from the top, then navigate to the "Configure" tab, and from the bottom select "Configure MCP Servers".&#x20;
