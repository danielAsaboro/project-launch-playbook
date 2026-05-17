# project-social-playbook

A launch-focused X/Twitter playbook skill for newly submitted Solana hackathon projects. It turns a raw project description into a sharp project-account narrative, a 4-week posting plan, community/event targets, and first-post drafts that do not read like generic AI launch copy.

## Install

```bash
npx skills add danielAsaboro/project-social-playbook
```

Works with Claude Code, Cursor, Codex, Gemini CLI, and other `npx skills` compatible agents.

## What it does

Give the skill your project name, what it does, who it is for, your tech stack, and optionally your team context or project X handle. It:

1. Matches the project to a launch archetype grounded in how strong Solana project accounts actually show up.
2. Derives the core story angle and why people should care right now.
3. Defines the audience wedges and proof points the account should keep repeating.
4. Produces a 4-week content calendar with hooks and draft copy.
5. Recommends spaces, AMAs, community channels, and reply targets.
6. Generates 5 example launch posts in the right project-account voice.

Outputs: a filled `playbook.md`, an importable `content-calendar.csv`, and a machine-readable `engagement-playbook.json`.

## Usage

After installing, ask in plain English:

```text
Build me a project social playbook for my Solana hackathon submission.
Project: [name]
What it does: [1-2 sentences]
Who it's for: [users]
Tech stack: [stack]
Project X handle: @yourproject
```

The skill asks for anything important that is missing, but it does not block on optional details.

## MCP server (optional)

The `mcp/` directory exposes `fetch_x_posts`, `web_search`, and `analyze_voice` as native tools. Without it, the skill falls back to the `scripts/` equivalents automatically.

Setup:

```bash
git clone https://github.com/danielAsaboro/project-social-playbook.git
cd project-social-playbook
cd mcp && npm install && cd ..
```

If you want MCP tool access instead of the built-in script fallbacks, add this to your local MCP config after installing the `mcp/` dependencies:

```json
{
  "mcpServers": {
    "project-social-playbook": {
      "command": "node",
      "args": ["./mcp/server.mjs"]
    }
  }
}
```

No `.env` file is required to start the MCP server. API keys are optional and only improve the quality of fetched X posts or web search results. If you want local env-file loading during manual development, create `.env` from `.env.example` and run `node --env-file=.env ./mcp/server.mjs` yourself.

## Environment variables

All optional.

| Variable | What it does |
|---|---|
| `TWITTERAPI_IO_KEY` | Fetch recent posts from a project X handle |
| `XQUIK_API_KEY` | Fallback X post fetcher |
| `RAPIDAPI_KEY` | Fallback X post fetcher |
| `TAVILY_API_KEY` | Web search for project/context enrichment |
| `EXA_API_KEY` | Web search fallback |
| `SERPAPI_KEY` | Web search fallback |

## License

MIT
