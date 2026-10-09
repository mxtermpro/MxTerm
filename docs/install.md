# Install MXterm Pro on macOS, Windows and Linux

![Four steps to install MXterm Pro: download for your system, open the installer, confirm the first launch prompt and install your agent CLIs](../assets/guides/install.webp)

> **In short:** download the build for your system, open it once, and install the coding-agent CLIs you want to run in panes. The macOS build is signed and notarized by Apple. The Windows installer and the Linux packages are not code-signed yet.

## macOS

Requires macOS 10.15 or later, Apple Silicon or Intel.

1. Download the `.dmg`.
2. Open it and drag **MXterm Pro** to **Applications**.
3. Launch MXterm Pro from Applications.
4. If macOS asks whether you want to open an app downloaded from the internet, click **Open**. That prompt is normal for any downloaded app.

If macOS blocks the app instead, open **System Settings → Privacy & Security** and choose **Open Anyway**.

**Homebrew** works too, through the tap in [`mxtermpro/homebrew-mxterm`](https://github.com/mxtermpro/homebrew-mxterm):

```sh
brew trust mxtermpro/mxterm && brew install --cask mxtermpro/mxterm/mxterm-pro
```

## Windows

Windows 10 or 11, 64-bit. There is no ARM64 build.

The installer is **not code-signed yet**, so the first time you run it Windows SmartScreen shows "Windows protected your PC" and lists the publisher as Unknown. Click **More info**, then **Run anyway**. Windows shows this for newer apps it has not seen many times; it is not a virus verdict. When MXterm Pro later updates itself, the warning should not appear again.

To check the file yourself, compare its SHA-256 with the value on the download page:

```powershell
Get-FileHash MXterm-Pro_<version>_x64-setup.exe -Algorithm SHA256
```

A few things work differently on Windows: Claude Code plan limits in the Token Meter read the macOS Keychain, so they are macOS-only; clicking a notification to jump to its pane and the Dock badge are not available; and a Control Room does not recognise an agent you start by hand in a plain pane.

## Linux (beta)

64-bit, Ubuntu 22.04 or later. Pick the `.deb` package for Ubuntu and Debian, or the **AppImage** for other distributions.

- The packages are not code-signed.
- Saved passwords and signing in need GNOME Keyring or KWallet to be running.
- Voice dictation and the in-app browser column are not available on Linux yet, so links open in your system browser.
- There is no automatic update on Linux: download the new version from the download page.

## Updates

On macOS and Windows, MXterm Pro updates itself from inside the app. Every release is listed in the [changelog](https://mxterm.net/changelog).

## Bring your own agents

MXterm Pro never installs a coding agent for you. Install the CLIs you want (for example `claude`, `codex` or `gemini`), sign in with your own account, and open them in a pane. The app recognises 27 agent CLIs and lists their commands on the [agents page](https://mxterm.net/agents).

## Your phone

The phone app lets you watch and steer the panes you share from your computer. Android is on Google Play (or as an APK on the download page). iPhone and iPad are in TestFlight beta. Pair with a 6-character code or a QR scan.

## Troubleshooting

- **"MXterm Pro can't be opened" on macOS:** use **System Settings → Privacy & Security → Open Anyway**.
- **SmartScreen blocks the installer on Windows:** **More info → Run anyway**, and verify the SHA-256 if you want to be sure.
- **No passwords saved on Linux:** start GNOME Keyring or KWallet first.
- **Anything else:** the [help center](https://mxterm.net/help) has first-launch and pairing answers.

## Next step

Open two panes and run two agents side by side: [Run Claude Code & Codex in split terminal panes](https://mxterm.net/blog/run-claude-code-and-codex-in-split-terminal).

---

## Read more on mxterm.net

- **Next step:** [Orchestrating Parallel AI Agents in Split Terminal Panes](https://mxterm.net/blog/run-claude-code-and-codex-in-split-terminal)
- [Help center](https://mxterm.net/help)
- **Get it:** [Download MXterm Pro](https://mxterm.net/download) for macOS, Windows and Linux, or see what [MXterm Pro](https://mxterm.net/) does in one page.

## Related guides

- [Control Room: run Claude Code, Codex and Gemini CLI together](control-room.md): Let agents message each other and hand off tasks.
- [Run Claude Code and Codex in split terminal panes](split-terminal.md): Two agents, two panes, one repo, no checkout fights.

[← All guides](README.md)
