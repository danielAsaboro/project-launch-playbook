# Scripts — Runtime helpers for the project-social-playbook skill

All scripts are Node ESM, zero external dependencies, and degrade gracefully.

## `fetch_x_posts.mjs`

Fetches recent posts from a project X handle.

```bash
node fetch_x_posts.mjs <handle> [--count 50]
```

The skill uses this for project-account grounding: cadence, proof density, and whether the account sounds too generic.

## `web_search.mjs`

Searches the web for project context.

```bash
node web_search.mjs "\"Project Name\" Solana launch thread" [--max 5]
```

Useful for docs pages, demo links, hackathon writeups, launch threads, and ecosystem mentions.

## `analyze_voice.mjs`

Extracts a posting fingerprint from a corpus of project-account posts.

```bash
node fetch_x_posts.mjs someproject | node analyze_voice.mjs
```

The output helps the skill judge whether the current account is too corporate, too technical, or too vague.

## Environment variables

All optional.

| Variable | Used by |
|---|---|
| `TWITTERAPI_IO_KEY` | `fetch_x_posts.mjs` |
| `RAPIDAPI_KEY` | `fetch_x_posts.mjs` |
| `TAVILY_API_KEY` | `web_search.mjs` |
| `EXA_API_KEY` | `web_search.mjs` |
| `SERPAPI_KEY` | `web_search.mjs` |
