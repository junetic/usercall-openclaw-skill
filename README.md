# openclaw user research skill

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

**2. Set the environment variable**

```bash
export USERCALL_API_KEY="your_key_here"
```

Add it to your `~/.zshrc` or `~/.bashrc` to make it permanent.

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
