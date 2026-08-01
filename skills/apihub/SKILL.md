---
name: apihub
description: Entry point for apihub — local/remote AI gateway with OpenAI-compatible REST for chat, image, TTS, embeddings, web search, web fetch. Use when the user mentions apihub, APIHUB_URL, or wants AI without writing provider boilerplate. This skill covers setup + indexes capability skills; fetch the relevant capability SKILL.md from the URLs below when needed.
---

# apihub

Local/remote AI gateway exposing OpenAI-compatible REST. One key, many providers, auto-fallback.

## Setup

```bash
export APIHUB_URL="http://localhost:20321"      # or VPS / tunnel URL
export APIHUB_KEY="sk-..."                      # from Dashboard → Keys (only if requireApiKey=true)
```

All requests: `${APIHUB_URL}/v1/...` with header `Authorization: Bearer ${APIHUB_KEY}` (omit if auth disabled).

Verify: `curl $APIHUB_URL/api/health` → `{"ok":true}`

## Discover models

```bash
curl $APIHUB_URL/v1/models                  # chat/LLM (default)
curl $APIHUB_URL/v1/models/image            # image-gen
curl $APIHUB_URL/v1/models/tts              # text-to-speech
curl $APIHUB_URL/v1/models/embedding        # embeddings
curl $APIHUB_URL/v1/models/web              # web search + fetch (entries have `kind` field)
curl $APIHUB_URL/v1/models/stt              # speech-to-text
curl $APIHUB_URL/v1/models/image-to-text    # vision
```

Use `data[].id` as `model` field in requests. Combos appear with `owned_by:"combo"`.

Response shape:
```json
{ "object": "list", "data": [
  { "id": "openai/gpt-5", "object": "model", "owned_by": "openai", "created": 1735000000 },
  { "id": "tavily/search", "object": "model", "kind": "webSearch", "owned_by": "tavily", "created": 1735000000 }
]}
```

## Capability skills

When the user needs a specific capability, fetch that skill's `SKILL.md` from its raw URL:

| Capability | Raw URL |
|---|---|
| Chat / code-gen | https://raw.githubusercontent.com/Gaoyubao0917/apihub/refs/heads/main/skills/apihub-chat/SKILL.md |
| Image generation | https://raw.githubusercontent.com/Gaoyubao0917/apihub/refs/heads/main/skills/apihub-image/SKILL.md |
| Text-to-speech | https://raw.githubusercontent.com/Gaoyubao0917/apihub/refs/heads/main/skills/apihub-tts/SKILL.md |
| Speech-to-text | https://raw.githubusercontent.com/Gaoyubao0917/apihub/refs/heads/main/skills/apihub-stt/SKILL.md |
| Embeddings | https://raw.githubusercontent.com/Gaoyubao0917/apihub/refs/heads/main/skills/apihub-embeddings/SKILL.md |
| Web search | https://raw.githubusercontent.com/Gaoyubao0917/apihub/refs/heads/main/skills/apihub-web-search/SKILL.md |
| Web fetch (URL → markdown) | https://raw.githubusercontent.com/Gaoyubao0917/apihub/refs/heads/main/skills/apihub-web-fetch/SKILL.md |

## Errors

- 401 → set/refresh `APIHUB_KEY` (Dashboard → Keys)
- 400 `Invalid model format` → check `model` exists in `/v1/models/<kind>`
- 503 `All accounts unavailable` → wait `retry-after` or add another provider account
