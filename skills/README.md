# apihub — Agent Skills

Drop-in skills for any AI agent (Claude, Cursor, ChatGPT, custom SDK). Just **copy a link** below and paste it to your AI — it will fetch the skill and use apihub for you.

> Tip: start with the **apihub** entry skill — it covers setup and links to all capability skills.

## Skills

| Capability | Copy link below and paste to your AI |
|---|---|
| **Entry / Setup** (start here) | https://raw.githubusercontent.com/decolua/apihub/refs/heads/master/skills/apihub/SKILL.md |
| Chat / code-gen | https://raw.githubusercontent.com/decolua/apihub/refs/heads/master/skills/apihub-chat/SKILL.md |
| Image generation | https://raw.githubusercontent.com/decolua/apihub/refs/heads/master/skills/apihub-image/SKILL.md |
| Video generation (xAI Grok Imagine) | https://raw.githubusercontent.com/decolua/apihub/refs/heads/master/skills/apihub-video/SKILL.md |
| Text-to-speech | https://raw.githubusercontent.com/decolua/apihub/refs/heads/master/skills/apihub-tts/SKILL.md |
| Speech-to-text | https://raw.githubusercontent.com/decolua/apihub/refs/heads/master/skills/apihub-stt/SKILL.md |
| Embeddings | https://raw.githubusercontent.com/decolua/apihub/refs/heads/master/skills/apihub-embeddings/SKILL.md |
| Web search | https://raw.githubusercontent.com/decolua/apihub/refs/heads/master/skills/apihub-web-search/SKILL.md |
| Web fetch (URL → markdown) | https://raw.githubusercontent.com/decolua/apihub/refs/heads/master/skills/apihub-web-fetch/SKILL.md |

## How to use

Paste to your AI (Claude, Cursor, ChatGPT, …):

```
Read this skill and use it: https://raw.githubusercontent.com/decolua/apihub/refs/heads/master/skills/apihub/SKILL.md
```

Then ask normally — *"generate an image of a cat"*, *"transcribe this URL"*, etc.

## Configure your shell once

```bash
export NINEROUTER_URL="http://localhost:20321"   # local default, or your VPS / tunnel URL
export NINEROUTER_KEY="sk-..."                   # from Dashboard → Keys (only if requireApiKey=true)
```

Verify: `curl $NINEROUTER_URL/api/health` → `{"ok":true}`.

## Links

- Source: https://github.com/decolua/apihub
- Dashboard: https://apihub.com
