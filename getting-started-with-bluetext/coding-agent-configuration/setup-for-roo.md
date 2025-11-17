# Setup for Roo

To connect Roo to your MCP, configure your mcp\_settings.json file to look like this:

```json
{
  "mcpServers": {
    "polytope": {
      "type": "streamable-http",
      "url": "http://localhost:31338/mcp",
      "disabled": false
    }
  }
}
```

To navigate to this file, from the Roo UI, "Views and More Actions" then "MCP Servers" then "Edit Global MCP".

**NOTE:** To ask questions switch to ask mode, and to generate code you should be in code mode. By default it is set to architect more, which will not help when generating code with Bluetext.
