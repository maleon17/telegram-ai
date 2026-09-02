# telegram-ai

Talk to **Claude Code** and **OpenAI Codex** from Telegram — on your existing
subscription, not a metered API key.

Four small, independent projects. They share design ideas (and a couple of
helper scripts) but no code coupling — pick the one you want:

|            | Bot-API bridge — you DM a bot | Userbot module — `.ask` in any chat |
|------------|-------------------------------|-------------------------------------|
| **Claude** | [claude-telegram-bridge](https://github.com/maleon17/claude-telegram-bridge) | [claude-ask](https://github.com/maleon17/claude-ask) |
| **Codex**  | [codex-telegram-bridge](https://github.com/maleon17/codex-telegram-bridge)   | [codex-ask](https://github.com/maleon17/codex-ask)   |

### Bridges (`*-telegram-bridge`)

A Bot-API bot you message directly. Holds one persistent CLI session per chat,
streams tool calls and progress live, and manages sessions, models and
permissions — plus, on the Claude side, multi-tenant isolated accounts. Runs
`claude -p` / `codex app-server` under your subscription login.

### Userbots (`*-ask`)

A Telethon / Hikka module loaded into your own account. `.ask <question>` in
**any** chat; the reply edits your own message in place, so it reads as if you
typed it. Carries a configurable "Jarvis" persona and real Telegram actions
(read history, send files, manage groups, auto-reply triggers) via MCP tools.

## Which one?

- Just want to chat with Claude/Codex from your phone → a **bridge**.
- Want it inline in group chats, answering as you → an **`*-ask`** userbot.
- They can run side by side; the only link is an optional file-channel
  (`bridge_exec.py`) for handing a task from one to the other.

## Install

Each repo is self-contained: `git clone`, run `setup.sh`, follow its README.
The userbots additionally need their backend (`*_watcher.py` plus the shared
`cmd_queue.py` HTTP relay) running on a host you control.

## Contributing

Fork the repo you're changing and open a PR there. If you run a modified copy
for your own deployment, keep it on a fork rather than a local divergence.
