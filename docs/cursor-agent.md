# Run Cursor Agent in a multi-pane terminal

![Four steps: open the composer and pick a folder, assign Cursor Agent panes, isolate features in git worktrees, then launch the panes](../assets/guides/cursor-agent.webp)

> **In short:** MXterm Pro's Cursor Agent template types `cursor-agent`, Cursor's agent CLI, into a real terminal pane. The app adds a status dot that shows whether the agent needs you, and opt-in git worktree isolation for when more than one agent touches the same repo. A Windows x64 build exists too.

## What this is

MXterm Pro does not intercept what `cursor-agent` does. It is a multi-terminal, multi-agent desktop app (Tauri 2 and Rust, not Electron) that opens a real PTY and types the command in. The `cursor` command is the editor's launcher and opens the Cursor window; `cursor-agent` is the CLI. This is for developers who already drive Cursor's agent from the command line and want it beside a second terminal, or beside Claude Code and Codex in the same workspace.

## Open a Cursor Agent pane

You need a `cursor-agent` executable on your `PATH` or in a common bin folder such as `/opt/homebrew/bin` or `~/.local/bin`. If MXterm Pro cannot find it, the Cursor Agent row in the composer shows "Not installed" instead of a count stepper.

1. Open the composer: it appears on first launch or when no saved tabs come back; otherwise press `⌘T`.
2. Pick your project folder. It becomes the working directory for every pane you create.
3. Use the stepper under **Cursor Agent** to assign panes to it. Leave the rest as plain shells or split them across other agents.
4. If you run more than one agent, tick **Isolate features in git worktrees**.
5. Press `⌘/Ctrl+Enter`. MXterm Pro types `cursor-agent` into that pane's shell.

Detection re-runs each time you reopen the composer, so if you install the CLI while MXterm Pro is running, close and reopen the composer. No app restart is needed.

## Status dot: how MXterm Pro knows what Cursor is doing

This is not a Cursor API integration. MXterm Pro matches patterns in the text already rendering in the pane, about every 300 milliseconds, and skips the read while the pane is idle. A line like `permission` or `do you want to` reads as **blocked**; `thinking…`, `generating…` or `working…` reads as **working**; a line ending in `cursor>` reads as **idle**. Right after a pane starts, the state is unknown for about three seconds while the startup screen is ignored.

The patterns for Cursor were written by hand and have not been checked against every Cursor session, so treat the dot as a hint. The same rule engine drives Claude Code, Codex, Gemini and the other agents: red for blocked, yellow for working, green for done. A background pane also chimes shortly after it blocks or finishes, and **Settings → Notifications** can turn that off for Cursor alone.

## Resuming a Cursor session

The composer's **Resume sessions** list reads Claude Code, Codex, Gemini and OpenCode history, but it does not scan Cursor's session store yet. To resume a Cursor conversation, run Cursor's own CLI by hand in the pane, for example `cursor-agent ls` to list past chats. After a relaunch your tabs and layout come back, but each pane starts a fresh terminal: a Cursor Agent pane starts `cursor-agent` again without its original brief, on purpose, so a task is not replayed against a worktree that has moved on.

## Run Cursor next to Claude Code or Codex

Tick **Isolate features in git worktrees** and every agent pane, Cursor included, gets its own checkout at `<repo>/.worktrees/<slug>` on a branch such as `swarm/azure-falcon`. MXterm Pro adds `.worktrees/` to your `.gitignore`. Cursor in `swarm/azure-falcon` and Claude Code in `swarm/mint-otter` then edit two different directories. Closing a pane never deletes its worktree, and an agent cannot remove one with uncommitted changes.

## Free and Pro

Worktree isolation is free. What the plan limits is scale: the Free plan runs a Control Room with 2 agents, so a room with Cursor, Claude Code and Codex together needs Pro. Panes are not limited on Free.

## Troubleshooting

- **"Not installed" in the composer:** install `cursor-agent`, then reopen the composer.
- **No colour right after the pane starts:** normal, detection waits about three seconds.
- **No Cursor entries under Resume sessions:** expected today.

## FAQ

**Does MXterm Pro modify or wrap the Cursor CLI?**
No. It starts a real PTY and types the template command into the shell. Status detection only reads the pane's rendered output.

**Can I run Cursor and Claude Code in the same window?**
Yes, each in its own pane, with its own worktree if isolation is on. A Cursor pane does not connect to a Control Room the way Claude Code or Codex do.

---

## Read more on mxterm.net

- **Full guide:** [Running Cursor Agent in a Multi-Pane Terminal on Mac](https://mxterm.net/blog/run-cursor-agent-in-mxterm-pro)
- [Supported agents](https://mxterm.net/agents)
- **Get it:** [Download MXterm Pro](https://mxterm.net/download) for macOS, Windows and Linux, or see what [MXterm Pro](https://mxterm.net/) does in one page.

## Related guides

- [Run Claude Code and Codex in split terminal panes](split-terminal.md): Two agents, two panes, one repo, no checkout fights.
- [One git worktree per AI agent](git-worktree.md): Give every agent pane its own branch and checkout.
- [Token Meter: Claude Code and Codex usage in the title bar](token-meter.md): Tokens used, read from your agents' own transcripts.

[← All guides](README.md)
