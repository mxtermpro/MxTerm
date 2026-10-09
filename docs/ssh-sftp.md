# SFTP GUI and remote editor beside your terminal

![The SFTP panel opens beside the terminal: edit in the Monaco editor, grep on the server and set chmod with a checkbox grid](../assets/guides/ssh-sftp.webp)

> **In short:** open a saved SSH host in MXterm Pro and a remote file manager is docked beside the terminal. Double-click a text file to edit it in a Monaco editor, search the server with remote grep, and set permissions with a chmod grid. Nothing in the panel is Pro-only.

## The panel

Open a saved host and the **FILES (SFTP)** panel is already beside your terminal, on the left by default. Collapse it with the panel-close button and it shrinks to a narrow vertical strip; click the strip to bring it back. Drag the divider to resize, and it can sit on the left or the right. It has a breadcrumb path bar: click a segment to jump up a level, or click into the bar to type a path. Each open host tab tracks its own path and file list, so two SSH tabs never show the wrong server's directory. The panel follows your terminal's `cd`, like MobaXterm's file panel, as long as the server's shell reports its folder (OSC 7). fish does this by itself; on bash or zsh, add one line to `~/.bashrc` or `~/.zshrc` on the server, which the panel offers to copy. The **Follow terminal folder** toggle turns it off.

## Edit remote files

Double-click a remote text file and it opens in a **Monaco editor** with real syntax highlighting, not a plain text area. About 90 extensions are treated as editable text, including `.env`, `nginx.conf`, `Dockerfile`, `.py`, `.ts`, `.php`, `.go` and `.yaml`; about 75 of them get language-specific highlighting, and `.txt`, `.log` and `.csv` open as plain text.

Shortcuts carry over from VS Code: `Cmd+Shift+F` find and replace, `Cmd+Option+F` format the document, `Cmd+/` comment a line, `Cmd+Shift+K` delete a line. `Cmd+S` writes the file back over SFTP. Before saving, MXterm Pro compares the file's modification time with the one it saw, and if something changed it on the server meanwhile, the save is refused and you choose what to do.

## Search the server and set permissions

**Remote Grep Search** runs `grep -rnI` on the server itself, with `.git`, `node_modules`, `vendor`, `storage`, `dist`, `build` and `.cache` excluded, so nothing is downloaded. It is a literal-string match (`-F`), not a regex. Results are capped at 100 matches per file and 60 in total, and clicking a hit opens the file.

Right-click a file or folder and choose **File permissions…**, or click the shield icon, for a 3×3 chmod grid: Owner, Group and Public against Read, Write and Execute, with an octal field and presets.

## Upload and download

Upload with a button or by dropping files from Finder. Downloads go to `~/Downloads`, from a row's button, the multi-select bar or the context menu. Images (`.png`, `.jpg`, `.gif`, `.svg`, `.webp` and more) open in a built-in viewer.

## Free and Pro

Everything above works on the Free plan. The Free plan saves up to 5 SSH hosts; Pro removes that cap.

## FAQ

**Is there a separate SFTP login?**
No. The panel reuses the SSH connection your tab already authenticated, so a password host that connects in the terminal also works in the file browser.

**Does MXterm Pro replace MobaXterm or Termius?**
They target different jobs. MXterm Pro is built around running several AI coding agents next to your servers; Termius syncs host lists across devices. Side-by-side pages: [vs MobaXterm](https://mxterm.net/vs/mobaxterm) and [vs Termius](https://mxterm.net/vs/termius).

---

## Read more on mxterm.net

- **Full guide:** [SFTP GUI Remote Editor for Mac: How to Browse, Edit and Chmod Remote Files](https://mxterm.net/blog/sftp-gui-remote-editor-mac)
- [SSH/SFTP page](https://mxterm.net/features/sftp-gui)
- [SSH and SFTP docs](https://mxterm.net/docs/ssh-and-sftp)
- **Get it:** [Download MXterm Pro](https://mxterm.net/download) for macOS, Windows and Linux, or see what [MXterm Pro](https://mxterm.net/) does in one page.

## Related guides

- [Manage 50+ SSH servers and cloud VMs on a Mac](manage-ssh-servers.md): Groups, import, broadcast and live server stats.
- [SSH port forwarding GUI: add local forwards on an open tab](ssh-port-forwarding.md): Add and cancel local forwards on an open SSH tab.
- [Docker build terminal on Mac, beside your SSH deploy](docker-ssh-deploy.md): Build in one pane, deploy over SSH in the next.

[← All guides](README.md)
