---
name: openclaw
description: Run real user interviews via Usercall. Use when you need qualitative feedback from real users — onboarding drop-off, feature confusion, pricing clarity, prototype testing, etc. Requires usercall MCP and a Usercall API key (https://app.usercall.co).
argument-hint: "[research goal or topic]"
---

You are helping the user run a real user interview study via Usercall.

**If the usercall MCP is not available or not configured:**

Tell the user:

> To run real user interviews, you need two things:
>
> **1. Get a free API key**
> Sign up at https://app.usercall.co → Home → Developer → Create API key
>
> **2. Add the Usercall MCP to your config**
>
> Claude Desktop (`~/Library/Application Support/Claude/claude_desktop_config.json`):
> ```json
> {
>   "mcpServers": {
>     "usercall": {
>       "command": "npx",
>       "args": ["-y", "@usercall/mcp"],
>       "env": {
>         "USERCALL_API_KEY": "your_key_here"
>       }
>     }
>   }
> }
> ```
>
> Cursor (`.cursor/mcp.json`):
> ```json
> {
>   "mcpServers": {
>     "usercall": {
>       "command": "npx",
>       "args": ["-y", "@usercall/mcp"],
>       "env": {
>         "USERCALL_API_KEY": "your_key_here"
>       }
>     }
>   }
> }
> ```
>
> Restart your MCP client, then run `/openclaw` again.

Stop here and wait for the user to set up the MCP.

---

**If the usercall MCP is available:**

If `$ARGUMENTS` is provided, use it as the research topic. Otherwise, ask the user:
- What do you want to learn from users? (e.g., "why users drop off during onboarding", "feedback on this prototype", "whether pricing is clear")
- Any relevant context about the product or users?
- Do you have a prototype or image URL to show during the interview? (optional)
- How many participants? (default: 1 to start, can increase later)

Then:

1. Call `create_study` with the collected inputs.

2. Present the result clearly:

```
Study created.

Share this interview link with your participants:
[interview_link]

When you have enough responses, ask me to get_study_results.
```

3. If the user asks for results, call `get_study_results` and present the themes with verbatim quotes formatted like:

```
Theme: [theme name]
[summary]

Quotes from participants:
- "[quote 1]"
- "[quote 2]"
```

4. If they want more interview slots, call `update_study` with the new `target_interviews` count.

Keep the interaction focused and practical. The goal is to get the user a shareable interview link as quickly as possible.
