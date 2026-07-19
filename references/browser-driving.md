# Driving the Flow in the Browser (bundled)

How to actually run the tasks live in Chrome, acting as the user. Bundled so the
skill carries its own execution method.

## One real prerequisite (can't be packaged)

Driving a real browser needs the **Claude-in-Chrome browser extension** installed
and connected, which exposes the `mcp__claude-in-chrome__*` tools. A skill file
can't ship a browser extension, so this is the one thing the operator's
environment must provide. If those tools aren't available, say so plainly and
offer the fallback: the user drives while you observe and direct
(share-screen / step-by-step), or they paste screenshots for you to evaluate.

## Loading the tools (they're usually deferred)

The Chrome tools are typically deferred — load them in a **single** `ToolSearch`
batch before use, never one at a time:

```
ToolSearch: select:mcp__claude-in-chrome__tabs_context_mcp,mcp__claude-in-chrome__navigate,mcp__claude-in-chrome__computer,mcp__claude-in-chrome__read_page,mcp__claude-in-chrome__tabs_create_mcp,mcp__claude-in-chrome__gif_creator,mcp__claude-in-chrome__read_console_messages
```

## Session start

1. Call `tabs_context_mcp` first to see existing tabs. Don't hijack the user's
   tabs — open a **new** tab with `tabs_create_mcp` for the flow under test
   (unless the user explicitly points you at an existing one).
2. Never reuse tab IDs from another session; if a tool errors that a tab is
   invalid, re-call `tabs_context_mcp` for fresh IDs.

## Behave like the persona, not the builder

- Take the path the persona would take, not the shortcut only an insider knows.
  If a real user would hunt for the button, hunt for it — the hunt is a finding.
- Narrate the lived experience out loud as you go: where your eye landed first,
  what you expected, where you hesitated, what confused you, what delighted you.
  This narration is the raw material of the report.
- Read the screen with `read_page` / screenshots the way a user reads it — top
  to bottom, most-prominent first. If the important thing isn't prominent, that's
  a hierarchy finding.

## Capture evidence as you go

- Screenshot key moments (landing, mid-task, success, any dead end).
- Record a **GIF** (`gif_creator`) for any multi-step flow worth showing back —
  capture a few frames before and after each action so playback is smooth. Name
  files for what they show (`vendor-search-to-detail.gif`), not `gif1`.
- For findings that need hard runtime proof (an error, a slow load), pull
  `read_console_messages` / network rather than asserting from behaviour alone.

## Safety

- **Never trigger native dialogs** (`alert`/`confirm`/`prompt`) — they freeze the
  extension and block all further commands. Avoid buttons that raise them; if one
  is unavoidable, warn the user first.
- Don't perform **destructive actions** on data the user is actively working with
  (delete/regenerate real records). Use throwaway records, or ask first.
- If the browser genuinely blocks — 2–3 failed attempts, no response, a page that
  won't load — **stop and report** what you tried and what went wrong. Don't loop
  or wander into unrelated pages.
