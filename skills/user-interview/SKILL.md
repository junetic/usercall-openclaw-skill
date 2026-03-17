---
name: user-interview
description: Run real user interviews via Usercall. Use when you need qualitative feedback from real users — onboarding drop-off, feature confusion, pricing clarity, prototype testing, etc. Requires usercall MCP configured with a Usercall API key (https://app.usercall.co).
argument-hint: "[research goal or topic]"
---

You are helping the user run a real user interview study via Usercall.

**If the usercall MCP tools (create_study, get_study_results) are not available:**

Tell the user:

> To use openclaw you need to complete two setup steps first:
>
> **Step 1 — Get a Usercall API key**
> Sign up at https://app.usercall.co → Home → Developer → Create API key
>
> **Step 2 — Install the usercall MCP**
> Add this to your MCP client config and restart:
>
> Claude Desktop (`~/Library/Application Support/Claude/claude_desktop_config.json`):
> ```json
> {
>   "mcpServers": {
>     "usercall": {
>       "command": "npx",
>       "args": ["-y", "@usercall/mcp"],
>       "env": { "USERCALL_API_KEY": "your_key_here" }
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
>       "env": { "USERCALL_API_KEY": "your_key_here" }
>     }
>   }
> }
> ```
>
> Once done, restart your client and run `/user-interview` again.

Stop here.

---

**If usercall MCP is available:**

If `$ARGUMENTS` is provided, use it as the research topic. Otherwise ask:
- What do you want to learn from users?
- Any context about the product or users?
- Do you have a prototype or image URL to show participants? (optional)
- How many participants? (default: 1, can increase later)

Then call `create_study` with the inputs and present the result:

```
Study created.

Share this interview link with your participants:
[interview_link]

When you have enough responses, ask me to fetch your results.
```

When the user asks for results, call `get_study_results` and present each theme with verbatim quotes:

```
Theme: [name]
[summary]

Quotes:
- "[quote]"
- "[quote]"
```

To add more slots, call `update_study` with a new `target_interviews` count.
To check status, call `get_study_status`.
