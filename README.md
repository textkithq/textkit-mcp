# TextKit MCP server

[TextKit](https://jointextkit.com?ref=gh-mcp) is an SMS API for developers. Its remote MCP server lets an agent send and receive SMS, verify phone numbers, buy numbers, load contacts, build segments, and run broadcasts and automations.

- URL: `https://mcp.jointextkit.com` (streamable HTTP)
- Auth: OAuth sign-in, or `Authorization: Bearer ssms_sk_...`
- Docs: https://jointextkit.com/docs/mcp?ref=gh-mcp

## Cline

Add to `cline_mcp_settings.json`:

```json
{
  "mcpServers": {
    "textkit": {
      "type": "streamableHttp",
      "url": "https://mcp.jointextkit.com",
      "headers": { "Authorization": "Bearer ssms_sk_test_..." },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

Get a key at [jointextkit.com/console](https://jointextkit.com/console?ref=gh-mcp). Test keys (`ssms_sk_test_...`) run in the sandbox. Step-by-step agent instructions: [llms-install.md](llms-install.md).

## Any other MCP client

```json
{
  "mcpServers": {
    "textkit": {
      "url": "https://mcp.jointextkit.com",
      "headers": { "Authorization": "Bearer ssms_sk_test_..." }
    }
  }
}
```

Clients with OAuth (Claude, Cursor, Gemini CLI) can drop `headers` and sign in instead.

## REST API

Base URL `https://api.jointextkit.com/v1`, OpenAPI at https://jointextkit.com/api/v1/openapi.yaml.
