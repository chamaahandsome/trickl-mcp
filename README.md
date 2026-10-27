# Trickl MCP Server

Trickl for AI assistants: full docs, setup plans, and sandbox tools to test purchases end to end.

This repository is the public home of the Trickl MCP server — documentation and client configuration for a hosted, remote MCP server. The server itself runs at Trickl; there is nothing to install or self-host from this repo.

- **Endpoint:** `https://api.trickl.app/mcp/dev` (streamable HTTP)
- **Website:** https://trickl.app
- **Docs:** https://www.trickl.app/docs
- **Official MCP Registry:** `app.trickl/trickl`
- **Glama:** https://glama.ai/mcp/connectors/app.trickl/trickl

## What it does

Connect Claude, Cursor, Cline, or any MCP client to Trickl. Your AI assistant gets:

- A step-by-step setup plan for integrating Trickl into your project
- Access to the full Trickl documentation
- Sandbox tools that run a test purchase end to end, so the assistant can check its own work

Trickl is a round-up payments platform: businesses let customers fund subscriptions, tickets, merch, and donations from spare change. Published pricing: 2.8% all-in for bank payments, 4.9% + 30¢ for cards, processing included, no setup or monthly fees.

## Tools

| Tool | What it does |
| --- | --- |
| `get_started` | Get a step-by-step Trickl integration plan for your project |
| `search_docs` | Search the Trickl documentation |
| `read_doc` | Read a documentation page |
| `check_api_key` | Validate an API key and see what it can access |
| `register_test_provider` | Register a sandbox provider account |
| `create_test_goal` | Create a sandbox funding goal |
| `get_goal` | Fetch a goal's current state |
| `cancel_test_goal` | Cancel a sandbox goal |
| `simulate_goal_event` | Simulate goal events (e.g. a payment) in the sandbox |
| `list_webhook_deliveries` | Inspect webhook deliveries for testing |

## Connect

Docs and planning tools work without a key. The sandbox tools need a **test key**: generate one in the Trickl dashboard (Developer tab) and send it as an `Authorization: Bearer tk_test_...` header. Live keys are refused on this endpoint — it is a sandbox/dev surface by design.

### Claude Code

```bash
claude mcp add --transport http trickl https://api.trickl.app/mcp/dev
```

With a test key:

```bash
claude mcp add --transport http trickl https://api.trickl.app/mcp/dev \
  --header "Authorization: Bearer tk_test_YOUR_KEY"
```

### Cursor / other MCP clients

Add a remote server with this configuration (also in [`.mcp.json`](.mcp.json)):

```json
{
  "mcpServers": {
    "trickl": {
      "url": "https://api.trickl.app/mcp/dev"
    }
  }
}
```

### Cline

See [llms-install.md](llms-install.md) for the Cline setup, written so an AI assistant can perform it for you.

## Support

hello@trickl.app
