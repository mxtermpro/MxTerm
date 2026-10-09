# One git worktree per AI agent

![Diagram: one repo fans out to three git worktrees, each on its own swarm branch, one per coding agent](../assets/guides/git-worktree.webp)

> **In short:** when two agents work in the same repository they share one working directory, and one agent's `git checkout` rewrites the files the other has open. With isolation on, each agent pane gets its own worktree and branch, which reduces the chance of checkouts clashing.

## Who needs it

A single agent alone in a repo has nothing to collide with, so isolation buys nothing. It matters once you run two or more agents against the same repository at the same time. The Swarm Task Orchestrator ships two presets built for that: "Full Swarm Trio (Lead, QA, Docs)" dispatches Claude Code, Codex and OpenCode together, and "Feature Duo (Dev + Tester)" pairs Claude Code with Codex. Both turn isolation on by default. You do not need a preset: open a new tab, choose the agents and tick the box yourself.

## Turn it on

The checkbox is **Isolate features in git worktrees**, in the New Workspace screen and in the Swarm Task Orchestrator dialog. It is off by default and works only in a git repository. In a folder that is not a git repo, the panes fall back to the plain folder with a notice.

When it is on, each new **agent** pane gets its own checkout inside `<repo>/.worktrees/<slug>`, on a freshly generated branch named `swarm/<adjective>-<noun>`, for example `swarm/brave-otter`. If the name is taken, MXterm Pro retries with a numeric suffix. It also adds `.worktrees/` to the repo's `.gitignore` so the throwaway checkouts are never committed by accident. A plain terminal pane with no agent opens at the repo root, untouched, and so does a pane you split off afterwards.

## What it prevents, and what it does not

Take "Feature Duo": Claude Code lands on its own branch and worktree, Codex on another. Without isolation, if Codex ran `git checkout` or `git stash` mid-task, the files Claude had open would change under it. With separate worktrees each agent has its own copy of every file, so that cannot happen.

Isolation does not remove every conflict. Two agents editing the same feature from different angles can still produce branches that need a human-reviewed merge, and MXterm Pro does not automate that. What it removes is narrow and mechanical: filesystem-level fights between agents.

## Add, merge and remove

- **Add mid-session:** an agent can spawn a new isolated worker pane for a delegated sub-task. This works only in a workspace created with isolation on.
- **Merge:** stays manual on purpose. Run `git merge swarm/brave-otter` from the main worktree, or push the branch and open a pull request.
- **Remove:** an agent can only remove a worktree with no uncommitted changes, with no override. From the UI, **Clean up worktrees…** next to the Git panel's worktree list clears them. Closing a pane never deletes its worktree.

## The manual alternative

You can do this by hand with `git worktree add` and `git worktree remove`, which is fine for one or two agents. What MXterm Pro removes is the bookkeeping as agents multiply: picking a unique branch name, provisioning the checkout, pointing the pane's working directory at it, and refusing to delete one that holds uncommitted work.

## Free and Pro

Worktree isolation works the same on both plans. What the plan limits is the size of a Control Room: Free runs 2 agents in a room, so "Feature Duo" fits and "Full Swarm Trio" in a single room needs Pro.

## FAQ

**Does it work with any agent?**
It applies to the agent panes you pick in the composer: Claude Code, Codex, Gemini CLI, OpenCode and the other built-in agents.

**Where are the worktrees?**
Inside the repo, at `<repo>/.worktrees/<slug>`, where the slug is the branch name with the slash written as a dash.

---

## Read more on mxterm.net

- **Full guide:** [Isolating Parallel AI Agents with Git Worktrees](https://mxterm.net/blog/isolate-ai-agents-with-git-worktrees)
- [Agents and Control Room docs](https://mxterm.net/docs/agents-and-war-room)
- **Get it:** [Download MXterm Pro](https://mxterm.net/download) for macOS, Windows and Linux, or see what [MXterm Pro](https://mxterm.net/) does in one page.

## Related guides

- [Control Room: run Claude Code, Codex and Gemini CLI together](control-room.md): Let agents message each other and hand off tasks.
- [Run Claude Code and Codex in split terminal panes](split-terminal.md): Two agents, two panes, one repo, no checkout fights.
- [Run Cursor Agent in a multi-pane terminal](cursor-agent.md): Cursor's CLI agent with a live status dot.

[← All guides](README.md)
