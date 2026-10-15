---
description: Read, search and crawl the live web with the MeshArc tools. Use when the user wants a web page's content, a web search with the pages read, a site's URLs or sections, a crawl of a site or section, a site watched on a schedule, or what changed on a site since the last crawl.
---

# Working with the web through MeshArc

The `mesharc` MCP server gives you 15 tools. Pick the smallest one that answers the question.

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
| Follow or stop something that came back as a job | `get_job`, `cancel_job` |

## Habits that save credits and time

- Before crawling a whole site, call `map_site` to see how it is laid out, then crawl only the section you need with path globs.
- Before setting up a project, call `get_project` with no project: it lists every setting and what it means. Setting names are exact; a guessed name is refused, so read the list instead of guessing.
- Listing projects, runs and pages, searching a project's pages, and changing settings cost nothing. Reading a page costs what reading it took; blocked pages and 404s cost nothing.
- A long crawl, run, batch or search can come back as a job. Follow it with `get_job` rather than starting it again.
- `delete_project` works only on a local server with an admin key. On the hosted server, tell the user to delete the project in the MeshArc app.

## Signing in

The first time a tool is used, Claude Code asks the user to connect: run `/mcp`, choose `mesharc`, and sign in to mesharc.dev in the browser. Access is read only unless the user allows changes when approving. If a tool that fetches pages or changes a project is refused for lack of access, tell the user to reconnect from `/mcp` and allow changes.
