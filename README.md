# MeshArc web crawler for Claude Code

A Claude Code plugin that adds [MeshArc](https://mesharc.dev) to Claude Code. Claude can then search the web and read the result pages, turn pages into clean markdown, map and crawl sites past bot walls, watch a site on a schedule, and tell you what changed since the last crawl.

It connects to the hosted MeshArc MCP server at `https://mcp.mesharc.dev/mcp`. There is nothing to install locally and no API key to copy: you sign in to mesharc.dev once.

## Install

In Claude Code:

```
/plugin marketplace add mesharc-org/claude-code-plugin
/plugin install mesharc@mesharc
```

Then run `/mcp`, choose `mesharc`, and sign in to mesharc.dev in the browser. Access is read only unless you allow changes when you approve.

From a terminal, the same two steps are:

```bash
claude plugin marketplace add mesharc-org/claude-code-plugin
claude plugin install mesharc@mesharc
```

## What you get

- **The `mesharc` MCP server**, with 21 tools: `search_web`, `scrape_urls`, `map_site`, `crawl_site`, `list_projects`, `get_project`, `create_project`, `update_project`, `delete_project`, `start_run`, `list_runs`, `list_pages`, `get_changes`, `run_agent`, `continue_agent`, `create_monitor`, `list_monitors`, `pause_monitor`, `get_monitor_rows`, `get_job` and `cancel_job`.
- **A skill, `mesharc-web`**, that tells Claude which tool fits which request and how to avoid spending credits it does not need to.

Try asking:

- "Read https://example.com/pricing and summarise the plans."
- "Map the sitemap of stripe.com and list its sections."
- "Crawl only the blog of hotspotseo.com, weekly, and tell me what changed since last week."
- "Find the monthly price of each plan on three competitors' pricing pages, with sources."
- "Search the news for our brand every morning and tell me what is new."

## Pricing

The plugin is free. The work is billed in MeshArc credits: the free plan has 1,000 credits and needs no card. A plain page read is 1 credit, and blocked pages and 404s cost nothing. See [mesharc.dev/pricing](https://mesharc.dev/pricing).

## Without the plugin

You can add the same server directly:

```bash
claude mcp add --transport http mesharc https://mcp.mesharc.dev/mcp
```

Setup for Claude Desktop, Cursor, VS Code and other clients is at [mesharc.dev/mcp](https://mesharc.dev/mcp).

## Links

- Docs: https://mesharc.dev/docs
- MCP server source: https://github.com/mesharc-org/mesharc-mcp
- Questions: [GitHub Discussions](https://github.com/orgs/mesharc-org/discussions)
- Security: security@mesharc.dev ([policy](https://mesharc.dev/legal/security))

## License

MIT
