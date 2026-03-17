# openclaw — user interviews inside Claude Code

A Claude Code skill that lets you run real user interviews without leaving your editor.

Ask a question. Get a shareable interview link. Come back for themes and verbatim quotes.

```
/openclaw why do users drop off during onboarding?
```

## What it does

- Creates a Usercall interview study from your research goal
- Returns a shareable link to send to participants
- Retrieves themes and verbatim quotes when interviews are complete
- Supports Figma prototypes and image mockups as visual stimulus

Powered by [Usercall](https://app.usercall.co) — AI-moderated voice interviews with real users.

## Install

```
/plugin install github:junetic/usercall-openclaw-skill
```

Then restart Claude Code.

## Setup (first use)

**1. Get an API key**

Sign up at [app.usercall.co](https://app.usercall.co) → Home → Developer → Create API key

**2. Add the MCP server to your config**

Claude Desktop (`~/Library/Application Support/Claude/claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "usercall": {
      "command": "npx",
      "args": ["-y", "@usercall/mcp"],
      "env": {
        "USERCALL_API_KEY": "your_key_here"
      }
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
      "env": {
        "USERCALL_API_KEY": "your_key_here"
      }
    }
  }
}
```

Restart your MCP client.

## Usage

```
/openclaw [research topic]
```

Examples:

```
/openclaw why do users drop off during onboarding?
/openclaw is our pricing page clear?
/openclaw feedback on this prototype: https://figma.com/proto/...
```

Without arguments, the skill walks you through it interactively.

## Requirements

- Claude Code (any version)
- Node.js 18+
- A Usercall API key ([free to start](https://app.usercall.co))

## License

MIT
