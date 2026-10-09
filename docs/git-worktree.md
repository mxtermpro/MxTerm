# One git worktree per AI agent

<img src="../assets/git-worktree.webp" alt="MXterm Pro git worktree isolation: each AI agent pane gets its own worktree and swarm branch so Claude Code, Codex and OpenCode do not clash on one checkout" width="100%" />

When two agents work in the same repository, they share one working directory. If one runs `git checkout` or `git stash`, the files the other has open change under it. A git worktree per agent gives each agent its own copy of the files on its own branch.

## Turn it on

It is an opt-in checkbox, off by default: **Isolate features in git worktrees**, in the new-tab composer. It works only in a git repository. In a folder that is not a git repo, the panes fall back to the plain folder with a notice.

When it is on, each new **agent** pane gets its own checkout in `<repo>/.worktrees/<slug>` on a freshly named branch such as `swarm/brave-otter`. MXterm Pro adds `.worktrees/` to the repo's `.gitignore`. A plain shell pane with no agent stays at the repo root. Panes you split off afterwards open in the workspace folder, not in a worktree of their own.

The Swarm Task Orchestrator presets "Full Swarm Trio (Lead, QA, Docs)" and "Feature Duo (Dev + Tester)" turn isolation on by default.

## What it prevents, and what it does not

It removes the filesystem-level fights: one agent's checkout rewriting files another agent has open. It does not merge anything. Two agents can still produce branches that need a human-reviewed merge, and MXterm Pro does not automate that. Merge the normal way: `git merge swarm/brave-otter`, or push and open a pull request.

## Cleaning up

An agent can only remove a worktree that has no uncommitted changes. From the UI, **Clean up worktrees…** next to the Git panel's worktree list removes them.

## Free and Pro

Worktree isolation works the same on both plans.

---

Full guide: [Isolate AI agents with git worktrees](https://mxterm.net/blog/isolate-ai-agents-with-git-worktrees) · See also [Control Room](control-room.md)
