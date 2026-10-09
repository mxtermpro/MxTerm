# Run Claude Code and Codex in split terminal panes

![Four steps: open a workspace on your repo, tick git worktree isolation, split panes with one agent each, then review and merge the branch](../assets/guides/split-terminal.webp)

> **In short:** open a workspace in MXterm Pro with **Isolate features in git worktrees** ticked, pick Claude Code for one pane and Codex for the other, and each agent works on its own branch instead of fighting over one checkout. Isolation reduces branch collisions. It does not stop two agents editing the same file.

## Why two agents in one repo usually go wrong

You open Claude Code in one tab and Codex in another, point both at the same working copy, and give them different jobs. One runs `git checkout -b feature-a` while the other is mid-edit on `main`, and now there are uncommitted changes on the wrong branch. Even on one branch, overlapping edits make merge conflicts you untangle by hand. Running them one after another avoids that but doubles your wait. The fix is to give each agent its own working copy on disk.

## Set it up

1. **Open a workspace on your repo.** Pick the folder on the Welcome / New Workspace screen. On macOS you can also drop the folder on the Dock icon.
2. **Tick "Isolate features in git worktrees".** It is off by default. It only helps inside a git repo. If the folder is not one, MXterm Pro tells you the agents will share it directly, and it no longer runs `git init` for you. Run `git init` yourself first if you want isolation.
3. **Split panes.** `Cmd+D` splits right, `Shift+Cmd+D` splits down (Windows: `Ctrl+D` and `Ctrl+Shift+D`), or set the pane count in the composer. To rearrange later, drag a pane header onto the edge of another pane. Dividers snap to 50/50 within about 3.5% of centre, and a double-click resets one.
4. **Launch one agent per pane.** Each agent pane you picked in the composer sits on its own branch, named like `swarm/brave-otter`, in `<repo>/.worktrees/<slug>`. A plain shell pane, or a pane you add later with a split, stays at the repo root.
5. **Give each agent a distinct task**, scoped to files that do not overlap: "refactor the auth middleware" in one pane, "update the settings UI" in the other.
6. **Review and merge from the repo root.** Merge the branch the normal way (`git merge`, or open a pull request). MXterm Pro does not merge for you.

## Broadcast one prompt to every pane

`Cmd+Shift+B` toggles **Broadcast Input** (Windows: `Ctrl+Shift+B`). Keystrokes typed into your active pane are mirrored to every other pane in the group, so one `npm test` or one instruction reaches all of them. It does not wait for one agent to finish before the next gets the command. Turn it off before typing anything pane-specific, or your answer to one agent's question goes to all of them.

## Add a Control Room when the agents need to talk

Split panes and worktrees keep agents apart on disk. A Control Room lets them message each other and hand off tasks. Toggle the right panel with `Alt+Cmd+B` on macOS and pick the Control Room tab. If you are typing in a pane, prompt delivery to that agent is held until you stop or click **Deliver now**.

## Watch the tokens

The Token Meter in the title bar gives each agent a row, with an hourly sparkline and a 7-day breakdown. It reads each agent's own transcripts on your machine, so it needs no API key.

## Free and Pro

Everything above works on the Free plan: unlimited panes, worktree isolation, broadcast and a Control Room with 2 agents. Two agents fit comfortably. Limits only show up when you add a third agent to one room, or manage many SSH hosts.

## When it does not work

- **The panes opened without worktrees.** The folder was not a git repo. Run `git init`, then create the workspace again. If the repo has no commits yet, MXterm Pro adds an "Initial commit" containing only an empty `.gitkeep` so the worktrees can be created.
- **Both agents keep touching the same files.** That is a task-scoping problem. Split the work along real module boundaries.
- **A broadcast reply went to the wrong pane.** The mode stays on until you toggle it off.

## FAQ

**Do I need git worktrees to run Claude Code and Codex in split panes?**
No. If they work in different repos, or you manage branch switches yourself, two plain panes are fine. Isolation matters when both agents work in the same repository at the same time.

**Can I use other agents?**
Yes. MXterm Pro recognises 27 agent CLIs, and any command-line tool runs in a plain pane. Worktree isolation applies to the agent panes you pick in the composer.

---

## Read more on mxterm.net

- **Full guide:** [Orchestrating Parallel AI Agents in Split Terminal Panes](https://mxterm.net/blog/run-claude-code-and-codex-in-split-terminal)
- [Panes docs](https://mxterm.net/docs/panes)
- **Get it:** [Download MXterm Pro](https://mxterm.net/download) for macOS, Windows and Linux, or see what [MXterm Pro](https://mxterm.net/) does in one page.

## Related guides

- [One git worktree per AI agent](git-worktree.md): Give every agent pane its own branch and checkout.
- [Control Room: run Claude Code, Codex and Gemini CLI together](control-room.md): Let agents message each other and hand off tasks.
- [Run Cursor Agent in a multi-pane terminal](cursor-agent.md): Cursor's CLI agent with a live status dot.

[← All guides](README.md)
