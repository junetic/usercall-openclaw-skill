# openclaw — user interviews from your editor

```
/user-interview why do users drop off during onboarding?
```

Ask a question. Get a shareable interview link. Come back for themes and verbatim quotes — without leaving your editor.

Powered by [Usercall](https://app.usercall.co).

---

## Install

```
/plugin install github:junetic/usercall-openclaw-skill
```

Restart your client.

## Setup

**1. Get a Usercall API key**

Sign up at [app.usercall.co](https://app.usercall.co) → Home → Developer → Create API key

**2. Install the usercall MCP**

Claude Desktop (`~/Library/Application Support/Claude/claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "usercall": {
      "command": "npx",
      "args": ["-y", "@usercall/mcp"],
      "env": { "USERCALL_API_KEY": "your_key_here" }
    }
  }
}
```

Cursor (`.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "usercall": {
      "command": "npx",
      "args": ["-y", "@usercall/mcp"],
      "env": { "USERCALL_API_KEY": "your_key_here" }
    }
  }
}
```

Restart your client.

## Usage

```
/user-interview [topic]
```

```
/user-interview why do users drop off during onboarding?
/user-interview is our pricing page clear?
/user-interview feedback on this prototype: https://figma.com/proto/...
```

Without arguments, it walks you through interactively.

## License

MIT
