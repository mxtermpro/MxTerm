# Token Meter: Claude Code and Codex usage in the title bar

![Diagram: a Token Meter chip in the title bar branching into last 5 hours, last 7 days, cache reads and opt-in plan limits](../assets/guides/token-meter.webp)

> **In short:** the Token Meter is a chip in MXterm Pro's title bar. By default it shows tokens **already used**, read from the transcripts your agents keep on your own disk, with no API key and nothing sent anywhere. It does not forecast how much you have left unless you switch on an opt-in plan-limit lookup.

## What it shows

Once an installed agent or a saved account key gives it something to show, the chip stays in the right-hand group of title-bar buttons while the app is open. It carries one figure: the **most constrained quota anywhere**, coloured by how close it is. If nothing you have configured publishes a quota, it shows the 5-hour token total of Claude Code, or of Codex when Claude Code is not installed. With no agent installed and only account balances, it shows the lowest USD balance.

Click it for a summary: one two-line row per provider you have set up, with its name and the reset clock that matters on the first line, and on the second its 5-hour and weekly bars where a limit is known, or today's spend and tokens where none is. The provider you pin in **Settings → Token Meter** is listed first (Claude Code by default). Each agent row expands to an hourly sparkline and a 7-day breakdown of input, output, cache and turns.

## Cache reads get their own line

Most tokens in a long agent session are cache reads: context the agent already sent, served back from the provider's cache on each turn. Counted together with everything else, they make a session look far bigger than it is. Given their own line, they stay out of the way, and you can see what the rest of the session actually came to.

## Where the numbers come from

For token counts the meter has one source: the transcript each agent keeps on your disk. Claude Code, Codex, Gemini CLI and omp record the token counts for every turn in theirs. It does not read OpenCode, so it shows nothing for it rather than a guess. There is no key to paste and no account to connect, and for token counts nothing is sent anywhere.

## Opt-in switches

These are off until you turn them on, and they do contact the provider:

- **Plan limits (Claude, macOS only).** Reads Claude Code's saved sign-in from the macOS Keychain and fetches your real plan usage from `api.anthropic.com`, at most once every five minutes.
- **Live Codex limits.** Reads Codex's ChatGPT sign-in from `~/.codex/auth.json` and sends it only to `chatgpt.com` to fetch the current 5-hour and weekly windows. Codex's session files also carry rate-limit readings, but only as fresh as your last Codex turn.
- **Account balances.** Paste an API key in **Settings → Token Meter** for a supported provider and it shows the balance, quota or spend that provider reports.

## What it will not show

It reports spend, not a prediction. Claude Code's transcripts do not record where a subscription stands, so a Claude percentage needs the Plan limits switch. If you run a single agent now and then you will not learn much; it is built for running Claude Code and Codex side by side, in split panes or in a Control Room.

## Free and Pro

The Token Meter is on the Free plan.

## FAQ

**Does the Token Meter send my usage anywhere?**
Not by default. Transcript reading is local. Only the opt-in switches contact a provider.

**Does Claude's plan-limit lookup work everywhere?**
No. It reads the macOS Keychain, so it is macOS-only. See the install guide for what else differs on Windows.

---

## Read more on mxterm.net

- **Full guide:** [Claude Code and Codex Token Usage: What the Token Meter Reads](https://mxterm.net/blog/claude-code-and-codex-token-usage)
- [Token Meter page](https://mxterm.net/features/token-meter)
- [Token Meter docs](https://mxterm.net/docs/token-meter)
- **Get it:** [Download MXterm Pro](https://mxterm.net/download) for macOS, Windows and Linux, or see what [MXterm Pro](https://mxterm.net/) does in one page.

## Related guides

- [Check AI API credit balance from your terminal](ai-credit-balance.md): Money, quota or spend: what each provider reports.
- [Control Room: run Claude Code, Codex and Gemini CLI together](control-room.md): Let agents message each other and hand off tasks.
- [Run Claude Code and Codex in split terminal panes](split-terminal.md): Two agents, two panes, one repo, no checkout fights.

[← All guides](README.md)
