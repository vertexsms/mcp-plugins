# VertexSMS

Cursor plugin that connects agents to [VertexSMS](https://vertexsms.com) through the official VertexSMS remote [Model Context Protocol](https://modelcontextprotocol.io/) server.

Send SMS, track delivery, check prices and balance, validate phone numbers and manage Sender IDs on your own VertexSMS account.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **VertexSMS**.
3. Click **Install**, then complete the VertexSMS sign-in prompt.

## MCP

```json
{
  "mcpServers": {
    "vertexsms": {
      "type": "http",
      "url": "https://mcp.vertexsms.com/mcp"
    }
  }
}
```

Auth is OAuth. Cursor prompts for VertexSMS sign-in when the plugin connects, and you approve the list of permissions you want to grant. There is no client ID, API key or secret to configure.

## Other clients

The `openai/` folder is the same connection packaged for the ChatGPT and Codex plugin directory, in the [Agent Plugins](https://agent-plugins.org) format: `plugin.json`, `mcp.json` and `assets/logo.png`. The server and the sign-in are the same as above.

## Before you connect

You need a VertexSMS account. Accounts are opened on request at [vertexsms.com](https://vertexsms.com/en/register-mcp).

## What agents can do

| Category | Capabilities | Effect |
| --- | --- | --- |
| Messaging | Send one SMS now or at a scheduled time, and check whether it was delivered | sending is billed and reaches a real phone |
| Prices and balance | SMS prices per country and operator in EUR, account balance | read-only |
| Phone numbers | Convert numbers to international format, tell mobile from landline, look up prefixes and network codes of a country | read-only |
| HLR | Live lookup of the operator of a number and whether it was ported | billed |
| Sender IDs | List Sender IDs and their status, submit a sender name for approval, register your own mobile number as a sender | registering changes the account |

Billed tools and tools that change the account are marked as destructive, so Cursor asks before each call.

The hosted server is the source of truth for tool names and schemas. Full reference: <https://vertexsms.com/en/mcp/tools>.

## Data

The server is a stateless bridge to the VertexSMS API. It stores no messages, phone numbers or credentials. Privacy policy: <https://vertexsms.com/en/privacy>.

## Support

<support@vertexsms.com>, <https://vertexsms.com/en/mcp/support>
