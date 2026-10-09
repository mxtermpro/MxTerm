# Control Room: run Claude Code, Codex and Gemini CLI together

A Control Room is a named room where AI coding agents, each in its own real terminal pane, message each other and hand off tasks while you watch. It was called War Room in older versions.

## When to use it

If you run one agent on one repo, skip it. It earns its keep once a task has two owners: a backend change that needs frontend sign-off, a bug that spans two services in two working copies, or one agent implementing while a second reviews the diff.

## How it works

1. Add an agent to a room with the **Control Room** button in its pane header, or use **Add all active panes** in the Members tab. Toggle the right panel with `Alt+Ctrl+B` (`⌥⌘B` on Mac).
2. The agent gets an intro message and is asked to call `list_peers` first. Until its first successful call it shows a "no handshake" badge and peers cannot message it.
3. Agents use four tools: `list_peers`, `send`, `read_inbox` and `claim` (an advisory file reservation).
4. `send` has two modes. **Probe** is for discussion and goes to the peer's inbox. **Execute** hands over a runnable task that is typed into the peer's terminal.

A room is a shared MCP server, so a Claude Code pane in one project and a Codex pane in another can share a room. MXterm Pro writes the MCP server into the config of the agents that support it.

## What it does not do

It is a message bus and a UI around it, not an autonomous planner. Nothing starts a debate until you prompt one agent to talk to its peer. A plain shell pane can join as a spectator but cannot receive an Execute. Every extra agent is another full CLI session using its own quota.

## Export

**Report (.md)** in the Discussion tab writes a Markdown report: a roster table, then the dialogue with each Execute and Probe tagged. The terminal ID, which doubles as the pane's MCP token, is left out on purpose so the file is safe to share.

## Free and Pro

The Free plan runs one Control Room with 2 agents. Pro removes the limit on rooms and members. The Report export works on both.

## Pair it with worktrees

Turn on [one git worktree per agent](git-worktree.md) so two agents in one repo do not edit the same checkout.

---

Full guide: [Control Room: Claude, Codex & Gemini in parallel](https://mxterm.net/blog/war-room-multi-agent-collaboration-guide) · [Control Room page](https://mxterm.net/features/war-room) · [Agents and Control Room docs](https://mxterm.net/docs/agents-and-war-room)
