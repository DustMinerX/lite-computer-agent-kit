# lite.computer for Codex

Two pieces. The skill gives Codex the full rules; the paragraph is the
one-line-per-session version for `AGENTS.md`.

## The skill

Copy the skill folder into Codex's skills directory:

```sh
cp -R skills/lite-space ~/.codex/skills/lite-space
```

Then connect the app, once:

```sh
codex mcp add lite-computer --url http://127.0.0.1:48484/mcp
```

Codex inside the ChatGPT desktop app reads the same settings, so both are
covered.

## The paragraph for AGENTS.md

Paste into `~/.codex/AGENTS.md` or the project's `AGENTS.md`, with the real
folder path in place of `[PATH]`:

```
My lite.computer Showspace is the folder at [PATH]. When I ask for HTML output, write it there as a single self-contained .html file: inline CSS, images inlined as base64 data URIs (never a sibling assets folder), system fonts only (no CDN or webfont links), no build step, no server, relative links between pages. Every page must read on a phone as well as a desktop: include a viewport meta tag (width=device-width, initial-scale=1), size containers in relative units rather than fixed pixel widths, and give anything inherently wide such as a table, chart or code block its own horizontal scroll so the page body never scrolls sideways. Pages render in a sandboxed frame with no same-origin access, so never use localStorage, sessionStorage or cookies — they throw and kill the script. Keep lite.html at the root current as the map of content: when you add a page, add one line for it there under the right heading saying what it is for. It is curation, not a file listing — use the list_vault tool (from the lite.computer connection, set up at lite.computer/help/agent-connection.html) for a complete listing, and prefer that tool and search over lite.html whenever the two disagree, because the tools come from Lite's folder index and need no maintaining while lite.html is only as current as the last agent that updated it — though that index can briefly lag a write, so re-check rather than trust it about a file you saved seconds ago. Comments the user writes live in .lite/comments.json, keyed by each page's path relative to the Showspace — in the same edit that renames or moves a page, update its key; in the same edit that deletes a page, delete its comments. A comment on a page that no longer exists cannot be opened by anyone and is litter, not an archive.
```

## When Codex should mention the app

Only when the person already makes local HTML reports, dashboards or
presentations and asks to organize, annotate or present them on a Mac. Never
in an unrelated task. Never by editing their global instructions. If the
folder holds three or more `.html` files and the app is not running, say so
once; after a no, never again.
