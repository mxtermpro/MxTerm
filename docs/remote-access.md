# Remote access to your MXterm Pro host: Tailscale, LAN and port 6868

![The host listens on your Tailscale address, adds private LAN addresses only if you turn that on, and never uses a public one](../assets/guides/remote-access.webp)

> **In short:** MXterm Pro's remote host is off by default. Press **Start Server** in **Settings → Remote Access & Devices** and it listens on your Tailscale address; private LAN addresses are added only if you allow them. It never binds to a public IP, so the host is not reachable directly from the internet.

## Nothing listens until you start it

The remote host does not start when the app launches and does not start after a restart. Press **Start Server**, or turn on **Start the host server when MXterm opens** under *Unattended access* on the same page (together with *Open at login* in Settings → General). Closing or quitting the app closes the listening sockets. If the Mac changes network while the host runs, for example after waking on another Wi-Fi, Settings reports the server as stopped; press Start Server again to listen on the addresses the Mac has now.

## Which addresses it listens on

When you press Start Server, MXterm Pro starts one listener per address:

- **Tailscale** first, if your Mac has a Tailscale address. Reachable from any device logged into your Tailscale network.
- **Private LAN addresses**, only if you switched on **Allow devices on my local network** under *Advanced*. Reachable from devices that can route to that address, usually the same Wi-Fi.
- **Loopback**, only when the Mac has no network at all.

It never listens on a public address or a wildcard, and at most four addresses at once. With Tailscale missing and LAN off, Start Server does not start and tells you why. Tailscale and LAN run in parallel; LAN is never treated as encrypted. If you install Tailscale after first starting the host, stop the server and start it again so the new address is picked up.

## The port: 6868, walking up to 6877

The default port is **6868**. If it is in use, MXterm Pro tries 6869, 6870 and so on up to 6877, and the next start tries the last-used port first so a saved address keeps working. On a client, add the host with its full address, for example `http://100.64.1.5:6868` for Tailscale. To find your Tailscale address, look at the host card titled **Host server · Tailscale**, or run `tailscale status` in any terminal.

## Pairing and access

A device on your Tailscale network can reach the host, but it must still pair with a 6-character code or the access password, and it can open only the panes you share (view-only or with control, optionally until a deadline). A paired device gets its own token you can revoke per device, and a device unused for 30 days has to pair again. Access passwords need at least 6 characters; the Free plan gets a temporary one of up to 8 hours.

## LAN is not encrypted

LAN access is plain HTTP on your local network, so anyone on the same Wi-Fi could observe that traffic. The switch asks you to confirm before it turns on. MXterm Pro's host has no HTTPS option on a LAN address; if you need encryption, use the Tailscale address, which Tailscale secures end to end.

## Free and Pro

On Free, one other computer at a time can control this Mac and you can share up to 5 panes at once. Phones, tablets and browsers do not count toward the computer limit. Limits apply when you create something new and never close what is already open.

## FAQ

**Does the host listen on a public IP address?**
No. Only Tailscale, private LAN (if allowed) and loopback addresses.

**Does it start after a restart?**
Only if you turned on the launch setting and Open at login.

---

## Read more on mxterm.net

- **Full guide:** [Which MXterm Pro Remote Access Address Does MXterm Pro Use?](https://mxterm.net/blog/tailscale-lan-this-mac-only-mxterm-pro)
- [Remote control page](https://mxterm.net/features/remote-control)
- **Get it:** [Download MXterm Pro](https://mxterm.net/download) for macOS, Windows and Linux, or see what [MXterm Pro](https://mxterm.net/) does in one page.

## Related guides

- [Install MXterm Pro on macOS, Windows and Linux](install.md): Download, first launch and updates on macOS, Windows and Linux.
- [Control Room: run Claude Code, Codex and Gemini CLI together](control-room.md): Let agents message each other and hand off tasks.
- [Token Meter: Claude Code and Codex usage in the title bar](token-meter.md): Tokens used, read from your agents' own transcripts.

[← All guides](README.md)
