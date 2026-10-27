# Installing the Trickl MCP server in Cline

Follow these steps exactly. The Trickl MCP server is a remote (streamable HTTP) server — there is no package to install and no command to run.

## Step 1: Open Cline's MCP settings

In VS Code with the Cline extension: open the Cline panel, click the **MCP Servers** icon, then the **Configure** tab (the `cline_mcp_settings.json` file). This file contains a JSON object with an `mcpServers` key.

## Step 2: Add the Trickl server

Add this entry inside `mcpServers`:

```json
"trickl": {
  "url": "https://api.trickl.app/mcp/dev",
  "transportType": "streamable-http",
  "disabled": false
}
```

Full example of the resulting file:

```json
{
  "mcpServers": {
    "trickl": {
      "url": "https://api.trickl.app/mcp/dev",
      "transportType": "streamable-http",
      "disabled": false
    }
  }
}
```

## Step 3 (optional): Add a sandbox test key

The documentation and planning tools (`get_started`, `search_docs`, `read_doc`) work with no key. The sandbox tools need a Trickl **test key**:

1. In the Trickl dashboard (https://trickl.app), open the **Developer** tab and generate a test key. Test keys start with `tk_test_`.
2. Add a `headers` object to the entry from Step 2:

```json
"trickl": {
  "url": "https://api.trickl.app/mcp/dev",
  "transportType": "streamable-http",
  "headers": {
    "Authorization": "Bearer tk_test_YOUR_KEY"
  },
  "disabled": false
}
```

Do not put a live key here — this endpoint refuses live keys; it is a sandbox/dev surface.

## Step 4: Verify

Save the settings file. Cline connects to the server and lists its tools. Ask Cline to call `get_started` — it should return a step-by-step plan for integrating Trickl into the current project. If the sandbox tools return an authorization error, check that the header from Step 3 is present and that the key starts with `tk_test_`.
