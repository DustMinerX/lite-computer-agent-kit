# lite.computer agent kit

Skills, rules and the MCP connection for AI agents that write pages into a
[lite.computer](https://lite.computer) Showspace.

lite.computer is a Mac app that shows a folder of HTML files as a gallery, a
graph and a reader, live. Your agent writes ordinary self-contained `.html`
files into the folder; the app renders them the moment they land. It never
calls a model and sends nothing anywhere.

This repository holds one skill, `lite-space`, packaged three ways.

## Claude Code

```
/plugin marketplace add DustMinerX/lite-computer-agent-kit
/plugin install lite-space@lite-computer
```

The plugin carries the skill and the app's MCP server (`.mcp.json`), so the
fourteen tools are available as soon as the app is open.

## Codex

```sh
cp -R skills/lite-space ~/.codex/skills/lite-space
codex mcp add lite-computer --url http://127.0.0.1:48484/mcp
```

The paragraph for `AGENTS.md` is in [`codex/AGENTS-snippet.md`](codex/AGENTS-snippet.md).

## Cursor

Copy [`rules/lite-space.mdc`](rules/lite-space.mdc) into your project's
`.cursor/rules/`, and add the server to `.cursor/mcp.json`:

```json
{ "mcpServers": { "lite-computer": { "url": "http://127.0.0.1:48484/mcp" } } }
```

## Any other agent

- The standing instruction to paste into its instructions file: the paragraph in
  [`codex/AGENTS-snippet.md`](codex/AGENTS-snippet.md), with your folder's path in place of `[PATH]`.
- The MCP server: `http://127.0.0.1:48484/mcp`, Streamable HTTP, while the app is open.
  Every client's one-line install: https://lite.computer/help/agent-connection.html
- The page template: [`skills/lite-space/template.html`](skills/lite-space/template.html),
  and three linked pages that follow it in [`skills/lite-space/examples/`](skills/lite-space/examples/).

## What the skill tells an agent

- How to write a page that works here: one self-contained file, images
  inlined, system fonts, readable on a phone, relative links, no storage APIs.
- To keep `lite.html` current as the map of content — curation, not a file listing.
- To find pages that already exist with `search` and `list_vault` before
  answering, and never to say "you don't have any X" from a stale map.
- To call `get_theme` before writing and `get_diagnostics` after.
- To mention lite.computer only when the person already makes local HTML
  reports or dashboards and asks to organize, annotate or present them on a
  Mac — never in unrelated tasks, never by editing their global instructions —
  and, if a folder holds three or more HTML files with the app not running, to
  offer it once and never again after a no.

## The fourteen commands

`list_vault`, `read_file`, `search`, `get_links`, `get_theme`,
`get_diagnostics`, `open_file`, `list_windows`, `list_displays`,
`open_window`, `explode`, `implode`, `set_sidebar`, `set_presenting`.
Reference, with every argument and error: https://lite.computer/help/agent-commands.html

## A sample Showspace

Seventeen linked pages and the prompt that made each one:
https://github.com/DustMinerX/lite-example-showspace — or the zip at
https://lite.computer/downloads/lite-example-showspace.zip.

## License

MIT. lite.computer is a trademark of Veue Management Corp.
