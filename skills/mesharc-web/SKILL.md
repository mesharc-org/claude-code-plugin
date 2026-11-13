---
description: Read, search and crawl the live web with the MeshArc tools. Use when the user wants a web page's content, a web search with the pages read, a site's URLs or sections, a crawl of a site or section, a site watched on a schedule, what changed on a site since the last crawl, a research question answered from several pages, or a search or question kept on a schedule.
---

# Working with the web through MeshArc


The `mesharc` MCP server gives you 21 tools. Pick the smallest one that answers the question.

| The user wants | Use |
|---|---|
| Results for a query, optionally with each page read | `search_web` |
| The content of one or more known URLs (up to 500) | `scrape_urls` |
| Every URL a site lists in its sitemaps, without fetching pages | `map_site` |
| One crawl of a site or a section | `crawl_site` |
| A site watched over time | `create_project`, then `start_run` |
| What changed since the last crawl | `get_changes` |
| Watched projects, their runs and pages | `list_projects`, `get_project`, `list_runs`, `list_pages` |
| Change a project's name, schedule or settings | `update_project` |
| A question that needs several pages or sites to answer | `run_agent` (carry on a run that hit its credit limit with `continue_agent`) |
| A search or a question kept on a schedule, reporting what changed | `create_monitor`; then `list_monitors`, `get_monitor_rows`, `pause_monitor` |
| Follow or stop something that came back as a job | `get_job`, `cancel_job` |

## Habits that save credits and time

- Before crawling a whole site, call `map_site` to see how it is laid out, then crawl only the section you need with path globs.
- Before setting up a project, call `get_project` with no project: it lists every setting and what it means. Setting names are exact; a guessed name is refused, so read the list instead of guessing.
- Listing projects, runs and pages, searching a project's pages, and changing settings cost nothing. Reading a page costs what reading it took; blocked pages and 404s cost nothing.
- A long crawl, run, batch or search can come back as a job. Follow it with `get_job` rather than starting it again.
- Reach for `run_agent` only when the answer needs several pages or sites: when you know what to fetch, `search_web` and `scrape_urls` are quicker and cheaper. An agent run always comes back as a job; check it with `get_job` every 30 to 60 seconds. `max_credits` caps the whole run (it pays the model's tokens as well as the pages); a cap under about 50 can stop a run before its first step, so for a small question use around 100.
- To watch a whole site's pages use a project; to keep watching a search or a question (mentions, rankings, prices) use `create_monitor`.
- `delete_project` works only on a local server with an admin key. On the hosted server, tell the user to delete the project in the MeshArc app.

## Signing in

The first time a tool is used, Claude Code asks the user to connect: run `/mcp`, choose `mesharc`, and sign in to mesharc.dev in the browser. Access is read only unless the user allows changes when approving. If a tool that fetches pages or changes a project is refused for lack of access, tell the user to reconnect from `/mcp` and allow changes.
