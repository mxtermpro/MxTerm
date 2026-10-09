<div align="center">

<img src="assets/icon.png" width="84" alt="MXterm Pro" />

# MXterm Pro — a terminal for AI coding agents, SSH and SFTP

**One native workspace for terminals, agents, SSH/SFTP and the work around your servers.** MXterm Pro is a desktop app for macOS, Windows and Linux that runs [Claude Code, Codex, Gemini CLI](https://mxterm.net/agents) and 24 other coding-agent CLIs in real terminal panes, next to your SSH sessions and a remote file browser — with a [Control Room](https://mxterm.net/features/war-room) so agents can talk to each other, and a [Token Meter](https://mxterm.net/features/token-meter) that shows how much of your usage window is gone.

[![Download for macOS, Windows and Linux](https://img.shields.io/badge/Download-macOS%20%7C%20Windows%20%7C%20Linux-15140f?style=for-the-badge&logo=apple&logoColor=white)](https://mxterm.net/download)
[![Website](https://img.shields.io/badge/mxterm.net-7b61ff?style=for-the-badge)](https://mxterm.net)
&nbsp;
![Free plan](https://img.shields.io/badge/Free%20plan-no%20pane%20limit-black)
![macOS notarized](https://img.shields.io/badge/macOS-Notarized-1f9d55)

</div>

---

## What it does

- **Real terminal panes, not a wrapper** — split, move between tabs and maximize; every pane is a real PTY. See [Claude Code and Codex in a split terminal](https://mxterm.net/blog/run-claude-code-and-codex-in-split-terminal).
- **A Control Room for several agents** — agents in separate panes join a shared room, message each other and hand off tasks, and you watch it live. → [Control Room guide](docs/control-room.md)
- **One git worktree per agent** — an opt-in setting gives each agent pane its own branch, so two agents in one repo stop fighting over the same checkout. → [Git worktrees guide](docs/git-worktree.md)
- **SSH and SFTP beside your terminal** — saved hosts, a remote file browser that sits next to the terminal, an in-app editor, remote search and a chmod grid. → [SSH & SFTP guide](docs/ssh-sftp.md)
- **Token Meter** — reads the token counts your agents already write to disk and shows them in the title bar. → [Token Meter guide](docs/token-meter.md)
- **Command Recipes** — a fixed set of ready-made Linux commands on `Cmd+J`. It is a keyword match, not an AI model.
- **Control from your phone** — pair a phone, tablet or browser by code and steer your panes from there. Phone control is free.

> **The problem it solves:** an agent is working in one terminal, the server you deploy to is in another, and you keep switching windows to see whether the first one is about to hit its usage limit. MXterm Pro puts the agents, the servers and the usage in one place.

## Download & install

MXterm Pro runs on macOS 10.15+ (Apple Silicon and Intel), Windows 10/11 x64 and Linux (64-bit, Ubuntu 22.04 or later; beta). On phones, Android is available; iPhone, iPad and Apple Watch are in beta.

| Method | How |
| --- | --- |
| **Direct (recommended)** | [**mxterm.net/download**](https://mxterm.net/download) → macOS `.dmg` (signed with an Apple Developer ID and notarized), Windows installer, or Linux `.deb` / AppImage. |
| **Homebrew (macOS)** | Via the [`homebrew-mxterm`](https://github.com/mxtermpro/homebrew-mxterm) tap — see that repo for the exact command. |

The Windows installer and the Linux packages are not code-signed yet; on Windows, SmartScreen may warn the first time. → [Install guide and first-launch warnings](docs/install.md)

MXterm Pro updates itself from inside the app on macOS and Windows; on Linux you download the new version.

## Works with

Claude Code · Codex · Gemini CLI · GitHub Copilot · OpenCode · Qwen Code · Amp · Cursor Agent · Grok — and 18 more (27 in total). You install each agent CLI and sign in with your own account; MXterm Pro never installs one for you. Full list with commands: [mxterm.net/agents](https://mxterm.net/agents).

## Guides

*Getting started* — [Install MXterm Pro](docs/install.md)

*Run several agents* — [Control Room](docs/control-room.md) · [One git worktree per agent](docs/git-worktree.md)

*Servers and files* — [SSH & SFTP: remote editor, search and chmod](docs/ssh-sftp.md)

*Watch your limits* — [Token Meter for Claude Code and Codex](docs/token-meter.md)

Full, up-to-date documentation lives on **mxterm.net**: [Docs](https://mxterm.net/docs) · [Blog](https://mxterm.net/blog) · [Help](https://mxterm.net/help) · [Changelog](https://mxterm.net/changelog)

## FAQ

**Is MXterm Pro free?**
Yes. The Free plan has no limit on terminal panes. It includes up to 5 saved SSH hosts, one Control Room with 2 agents, git worktree isolation and the Token Meter. Pro removes the limits on hosts, rooms and members. It is a one-time payment, not a subscription — see [pricing](https://mxterm.net/pricing).

**Does MXterm Pro install Claude Code or Codex for me?**
No. Install the agent CLIs you want and sign in with your own account. MXterm Pro runs them in panes.

**Does the Token Meter send my usage anywhere?**
By default it only reads the transcripts each agent already keeps on your disk. For the token counts, nothing is sent anywhere. Optional switches for plan limits and account balances do contact the provider, and are off until you turn them on. → [details](docs/token-meter.md)

**Does it run on Windows and Linux?**
Yes. Windows 10/11 x64 is public; its installer is not code-signed yet, so SmartScreen shows an Unknown publisher on first run. Linux (Ubuntu 22.04 or later, `.deb` or AppImage) is a beta.

**How does it compare with iTerm2, MobaXterm, Termius and Warp?**
iTerm2 and MobaXterm are excellent terminals; Termius is a strong SSH/SFTP client. MXterm Pro is built for running several AI coding agents next to your servers. Side-by-side pages: [vs iTerm2](https://mxterm.net/vs/iterm2) · [vs MobaXterm](https://mxterm.net/vs/mobaxterm) · [vs Termius](https://mxterm.net/vs/termius).

## Alternatives & related projects

MXterm Pro is a closed-source desktop app. If you want something fully open-source, or simpler, these are good places to start:

- [iTerm2](https://github.com/gnachman/iTerm2) — the long-standing macOS terminal: GPL v2, split panes, tmux integration, Python API.
- [tmux](https://github.com/tmux/tmux) — the standard terminal multiplexer: free, scriptable, runs everywhere.

Browse more in the [`terminal-emulator`](https://github.com/topics/terminal-emulator) and [`ai-agents`](https://github.com/topics/ai-agents) topics on GitHub.

## Support

- **Bugs / help:** [open an issue](https://github.com/mxtermpro/Mxterm/issues/new/choose)
- **Questions / ideas:** [Discussions](https://github.com/mxtermpro/Mxterm/discussions)
- **Everything else:** [mxterm.net](https://mxterm.net) · support@mxterm.net

---

<div align="center">
<sub>MXterm Pro is a closed-source app. This repository hosts its releases, docs and community support.</sub>
</div>
