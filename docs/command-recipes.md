# Command Recipes: ready-made Linux commands on Cmd+J

![Cmd+J matches keywords to ready-made Linux commands for ten kinds of task, with no AI model involved](../assets/guides/command-recipes.webp)

> **In short:** press `Cmd+J` (macOS), type a task in English or Vietnamese such as "find log files bigger than 50MB", and MXterm Pro returns a fixed, ready-made Linux command. No AI model is involved, matching runs inside the app, and nothing you type leaves your computer.

## How it works

`Cmd+J` opens a small prompt over your active pane, local or SSH. Type a request and click **Find Recipe**. MXterm Pro scores your words against the keyword groups of its built-in recipes and returns the best match. The command is fixed, so nothing is written on the fly. On Windows the shortcut is `Ctrl+J`, which has not been verified there.

The ten categories are big files and logs, memory/RAM, CPU load, disk space, open ports, Docker, Nginx, firewall (UFW) rules, system logs and reboot. For example:

| You type | You get |
| --- | --- |
| find large log files | `find /var/log -type f -name "*.log" -size +50M -exec ls -lh {} + 2>/dev/null \| sort -rh -k5 \| head -n 20` |
| what is using my RAM | `ps aux --sort=-%mem \| head -n 15` |
| disk usage | `df -h`, then `du -sh /* \| sort -h` |
| what is listening on port 8080 | `ss -tulpn \| grep :8080 \|\| lsof -i :8080` |
| clean up docker | `docker system prune -af --volumes` |
| test nginx config | `nginx -t && systemctl reload nginx` |
| open port 443 | `ufw allow 443/tcp && ufw reload && ufw status` |

Port numbers are pulled out of your sentence, so "is anything using port 443" carries the 443 into the command. The result card has **Copy** and **Insert & Run In Terminal**; the second types the command into the focused pane and presses Enter straight away, with no second confirmation. Read the command first, especially `docker system prune -af --volumes` and `sudo reboot`.

## Who it is for

People who SSH into the same handful of Linux servers and keep re-typing or re-Googling the same operational one-liners. These are Linux commands, so many will not run in a local macOS or Windows shell. It is not for describing a novel one-off task and getting back whatever bash it implies. If your wording does not land in one of the ten categories, it says "No recipe matches that" instead of guessing.

## How matching works

Your prompt is lowercased and, for Vietnamese, stripped of tone marks, so "bộ nhớ" and "bo nho" hit the same RAM recipe. Scores decide the winner; on a tie the recipe with more keyword groups wins, then the one listed first. It matches words, not meaning, and it is tuned for English and Vietnamese only.

## A separate safety net: the guardrail

Independent of Command Recipes, MXterm Pro checks commands typed or pasted into any pane against a fixed list of well-known destructive shapes: `rm -rf /`, `rm -rf ~`, `rm -rf *`, `rm -f /`, `git push --force`, `mkfs`, `dd if=`, `drop database`, `drop table` and the classic fork bomb. A match opens a **Security Guardrail Interception** dialog with **Block & Cancel** and **Approve & Execute**, and nothing reaches the shell until you choose. It is a pattern list, not an AI reviewing intent: a destructive command phrased differently will not trip it.

## Free and Pro

Command Recipes has no licence check and works the same on both plans.

## FAQ

**Does it send what I type or my SSH credentials anywhere?**
No. Matching is a local function with no network call, and SSH tabs run the system `ssh`, which Command Recipes never sees.

**Is it the same as Warp AI or GitHub Copilot CLI?**
No. Those call a language model and can answer open-ended requests, with the prompt leaving your machine. Command Recipes is narrower but instant and offline.

---

## Read more on mxterm.net

- **Full guide:** [How Command Recipes Works: Ready-Made Linux Commands, Matched by Keyword](https://mxterm.net/blog/command-recipes-linux-commands)
- [Command Recipes page](https://mxterm.net/features/command-recipes)
- **Get it:** [Download MXterm Pro](https://mxterm.net/download) for macOS, Windows and Linux, or see what [MXterm Pro](https://mxterm.net/) does in one page.

## Related guides

- [Manage 50+ SSH servers and cloud VMs on a Mac](manage-ssh-servers.md): Groups, import, broadcast and live server stats.
- [SFTP GUI and remote editor beside your terminal](ssh-sftp.md): Edit, search and chmod remote files beside the terminal.
- [Docker build terminal on Mac, beside your SSH deploy](docker-ssh-deploy.md): Build in one pane, deploy over SSH in the next.

[← All guides](README.md)
