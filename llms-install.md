# Installing the TextKit MCP server in Cline

TextKit is a remote MCP server. There is nothing to download, build or run locally.

- Server URL: `https://mcp.jointextkit.com`
- Transport: streamable HTTP (`"type": "streamableHttp"`)
- Auth: `Authorization: Bearer <TextKit API key>`

## Steps

1. Ask the user for a TextKit API key. Keys start with `ssms_sk_`. They can create one at https://jointextkit.com/console (API keys page). Recommend a test key (`ssms_sk_test_...`) first: it runs in the sandbox and no real phone gets a text.
2. Add this entry to `cline_mcp_settings.json` under `mcpServers`, with the user's key in place of `ssms_sk_test_...`. Keep any servers already there.

```json
{
  "mcpServers": {
    "textkit": {
      "type": "streamableHttp",
      "url": "https://mcp.jointextkit.com",
      "headers": {
        "Authorization": "Bearer ssms_sk_test_..."
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

3. Set `"type": "streamableHttp"` explicitly. Without it Cline uses the legacy SSE transport and the connection fails.
4. Check the connection: call `get_balance` (read-only). A result with the account balance means it works. A 401 `invalid_api_key` means the key was pasted wrong.

## Notes for using the tools

- Phone numbers are E.164, e.g. `+15551234567`.
- Before texting many people, call `send_batch` with `dry_run: true` and show the user the count, cost and skipped recipients. Send only after they approve.
- Leave `autoApprove` empty unless the user asks; sending texts costs money with a live key.

Docs: https://jointextkit.com/docs/mcp
