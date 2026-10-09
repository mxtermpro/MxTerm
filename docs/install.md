# Install MXterm Pro

Download MXterm Pro from [mxterm.net/download](https://mxterm.net/download). It runs on macOS 10.15 or later (Apple Silicon and Intel), Windows 10/11 x64 and Linux (64-bit, Ubuntu 22.04 or later, beta).

## macOS

MXterm Pro for macOS is signed with an Apple Developer ID and notarized by Apple.

1. Download the `.dmg`.
2. Open it and drag **MXterm Pro** to **Applications**.
3. Launch MXterm Pro from Applications.
4. If macOS asks whether you want to open an app downloaded from the internet, click **Open**. This prompt is normal for any app downloaded from the internet.

If macOS blocks the app instead, open **System Settings → Privacy & Security** and choose **Open Anyway**.

## Windows

Windows 10/11, 64-bit. The installer is **not code-signed yet**, so the first time you run it Windows SmartScreen shows "Windows protected your PC" and lists the publisher as Unknown. Click **More info**, then **Run anyway**. Windows shows this for newer apps it has not seen many times; it is not a virus verdict. The download page lists the file's SHA-256 so you can check it yourself with `Get-FileHash` in PowerShell.

A few things are not available on Windows: Claude Code plan limits in the Token Meter (they read the macOS Keychain), click-a-notification-to-jump-to-its-pane, and recognising an agent you start by hand in a plain pane.

## Linux

Beta. Choose the `.deb` package for Ubuntu and Debian, or the AppImage for other distributions. The packages are not code-signed. Saved passwords and signing in need GNOME Keyring or KWallet to be running. Voice dictation and the in-app browser column are not available on Linux yet, and there is no automatic update on Linux: download the new version from the download page.

## Updates

On macOS and Windows, MXterm Pro updates itself from inside the app.

## Your agents

MXterm Pro does not install coding agents for you. Install the CLIs you want (for example Claude Code or Codex) and sign in with your own account, then open them in a pane. See the [supported agents](https://mxterm.net/agents).

## Phone

Android is on [Google Play](https://mxterm.net/download). iPhone and iPad are in TestFlight beta. Pair by a 6-character code or a QR scan.

---

Full install notes and checksums: [mxterm.net/download](https://mxterm.net/download) · Help: [mxterm.net/help](https://mxterm.net/help)
