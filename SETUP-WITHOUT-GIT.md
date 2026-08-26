# Setup Without Git

Set up Engineering Leader OS without a GitHub account, without Git, and without a terminal. You download the template as a ZIP file, keep it in a cloud-synced folder for backup, and run it through the Claude desktop app.

This path is for you if you want the system but don't work with Git day to day. If you're comfortable with Git, use the [version-controlled setup](README.md#quick-start) instead — it gives you history you can diff, which this path doesn't.

**Time:** about 30 minutes, most of it downloads and sign-ins.

---

## What You Get, And What You Give Up

| | Version-controlled setup | This setup |
|---|---|---|
| GitHub account | Required | Not needed |
| Git commands | A few | None |
| Terminal | Yes | None |
| Backup | GitHub | Your cloud drive |
| History of your notes | Full — every version, diffable | Whatever your cloud drive keeps per file |
| Getting template updates later | `git pull` | Download again and merge by hand |

The real trade is history. Git lets you ask "what did `memory.md` say six months ago?" and get an exact answer. A cloud drive keeps per-file versions for a while, which is backup but not the same thing.

---

## Requirements

Get these before you start.

- **A Claude paid plan** — Pro, Max, Team, or Enterprise. Claude Code doesn't run on the free tier.
- **A cloud drive with a desktop app** — Google Drive, iCloud Drive, OneDrive, or Dropbox. You need the desktop app that syncs a real folder on your computer, not just the website.
- **On Windows only: [Git for Windows](https://git-scm.com/downloads/win).** You never type a Git command, but the Claude desktop app won't start local sessions without it. Install it and restart the app. Most Macs already include Git.

---

## Download The Template

1. On this repository's GitHub page, click the green **Code** button, then **Download ZIP**.
2. Unzip the file. You get a folder whose name ends in `-main`.
3. Rename the folder to `engineering-leader-os`.

No account or sign-in is needed for this step.

---

## Back Up The Vault To Your Cloud Drive

Put the vault under cloud backup so every change is saved as you work. Where the folder has to live depends on your provider.

### Google Drive

Drive can back up a folder that stays where it already is. You don't move anything.

1. Install [Google Drive for desktop](https://support.google.com/drive/answer/10838124) and sign in.
2. Open Drive from the menu bar or system tray, then click the gear icon and choose **Preferences**.
3. Select **My Mac** (or **My PC**) — the pane labeled *Folders from your computer*.
4. Click **Add folder** and choose your `engineering-leader-os` folder.
5. Confirm the folder is listed and reports a size rather than an error.

The folder now appears under **Computers** in Drive on the web. Folders added this way are always kept in full on your computer — per Google, *"Local folders or your desktop can only be mirrored"* — so there is no streaming setting to get wrong.

> [!NOTE]
> This backs up the folder from **this** computer. Google doesn't document it as a way to sync one folder across several machines. If you want the vault on more than one computer, put it inside `~/Google Drive/My Drive/` instead, and set **Preferences → Google Drive → Mirror files** so a full copy stays on disk. The default, **Stream files**, keeps files in the cloud until opened, which leaves Obsidian and Claude Code scanning a folder whose contents aren't there.

### iCloud Drive, OneDrive, or Dropbox

These sync a folder they own, so the vault has to live inside it.

1. Install the provider's desktop app and sign in.
2. Move the `engineering-leader-os` folder into the synced folder — your iCloud Drive folder, `~/OneDrive/`, or `~/Dropbox/`.
3. Wait for the folder to finish syncing before you open it. Don't start while files still show as pending.
4. If the app offers to save space by keeping files online-only, turn that off for this folder. Obsidian and Claude Code both need the files present on disk.

### What Cloud Backup Does And Doesn't Cover

> [!WARNING]
> **A cloud drive syncs. It does not archive.** If you delete a note on your computer, it's deleted in the cloud too. Every provider keeps per-file version history for a limited window — "Manage versions" in Drive, "Version history" in OneDrive and Dropbox — but don't treat sync as protection against deleting something.

> [!WARNING]
> **Consider which account you're syncing to.** This vault fills up with 1:1 notes, performance ratings, and flight-risk assessments about named people. Storing that in a personal cloud account may conflict with your employer's data policy; storing it in your corporate account means your employer can access it. Neither is automatically wrong. Pick deliberately.

---

## Install Obsidian And Open The Vault

1. Download and install [Obsidian](https://obsidian.md). It's free, and you don't need an account.
2. Open Obsidian. On the start screen, click **Open folder as vault**.
3. Select your `engineering-leader-os` folder.
4. When Obsidian asks whether you trust the author, choose **Trust author and enable plugins**. The vault ships no plugins — this only enables the ones you add yourself later.

You should now see the folder tree — `frameworks`, `goals`, `people`, `reviews`, and the rest — in the left sidebar.

---

## Install The Claude Desktop App

1. Download the installer for your platform from the [Claude Code desktop guide](https://code.claude.com/docs/en/desktop-quickstart). macOS and Windows have direct downloads there; Linux is in beta.
2. Install and launch it, then sign in with your Anthropic account.
3. Click the **Code** tab at the top center.

If the Code tab asks you to upgrade, your plan doesn't include Claude Code yet — you need Pro, Max, Team, or Enterprise.

You don't install Node.js or anything from a terminal. The desktop app includes Claude Code.

---

## Point Claude At Your Vault

1. In the **Code** tab, choose **Local** as the environment.
2. Click **Select folder** and choose your `engineering-leader-os` folder.
3. Select a model from the dropdown next to the send button.
4. Set the permission mode next to the send button to **Manual** for your first few sessions. Claude then shows you each file change and waits for your approval. Switch to **Accept edits** later, once you trust what it does.

Type this to confirm everything is connected:

```
Read CLAUDE.md and tell me what this vault is set up to do.
```

Claude should describe the system and its commands. If it can't find the file, you selected the wrong folder — check that the folder you picked contains `CLAUDE.md` directly, not one level up.

---

## Make It Yours

The template ships with blanks. Run the guided setup:

```
Read BOOTSTRAP.md and walk me through Phase 1.
```

Claude interviews you and fills in your name, role, teams, and people. Answer in your own words — it writes the files.

Then look for placeholders it missed. Search the vault in Obsidian (**Ctrl+Shift+F** on Windows, **Cmd+Shift+F** on Mac) for `[YOUR_` and `[NUMBER_OF_` and fill in what comes up.

---

## Run Your First Command

Type this in the Code tab:

```
/daily-checkin
```

You get a morning briefing built from your goals, your teams, and anything due. It's display-only the first time — it won't write a file until you say so.

From here, see [The Cadences](README.md#the-cadences) in the README for the full set of commands.

---

## Optional: Connect Your Calendar, Jira, Or Slack

These are optional. Every command works without them; they just replace manual pasting.

In the Code tab, click the **+** button next to the prompt box, select **Plugins**, and install what you need — `atlassian` for Jira and Confluence, `slack` for reading channels. Google Calendar and Drive connect through **Connectors** rather than plugins.

Without a calendar connection, `/calendar` and `/daily-checkin` ask you to paste your agenda, and everything else proceeds normally.

---

## Getting Template Updates Later

This path has no automatic update. When the template changes and you want the new version:

1. Download the ZIP again.
2. Copy only the parts you haven't personalized — usually `.claude/skills/` and `frameworks/`.
3. Leave your own content alone: `memory.md`, `writing_style.md`, `principles.md`, `goals/`, `people/`, `reviews/`, and `teams/`.

Copy your whole vault to a folder outside your cloud drive first, so you have a snapshot that a bad copy-paste can't reach.

---

## Troubleshooting

**The Code tab says "Git is required."**
You're on Windows without Git. Install [Git for Windows](https://git-scm.com/downloads/win), then restart Claude completely.

**Claude says it can't find `CLAUDE.md`.**
The selected folder is wrong. In the Code tab, select the folder again and pick the one that contains `CLAUDE.md` directly.

**Obsidian shows an empty vault, or files load slowly.**
Your cloud app is keeping files online-only instead of on disk. On Google Drive, this happens when the vault sits in `My Drive` with **Stream files** selected — switch to **Mirror files**, or back the folder up through *Folders from your computer* instead. On OneDrive or Dropbox, turn off the online-only or "save space" option for this folder.

**Files appear with `(1)` in the name, or you see "conflicted copy".**
Your cloud drive hit a sync conflict, usually because two devices edited at once or the app was closed mid-sync. Open both versions, keep the correct text, and delete the other. To avoid it: let sync finish before switching machines, and don't run Claude on two computers against the same vault at the same time.

**A command asks for a Jira ID or a cloud ID you don't have.**
That command needs a connector you haven't set up. Skip it — `/daily-checkin`, `/weekly-review`, `/prep-1on1`, `/draft-message`, and `/log-decision` all work with no external connections.

---

## If You Outgrow This

Nothing here blocks you from moving to the version-controlled setup later. Your vault is a plain folder of markdown files, so you can create a private GitHub repository and push the same folder into it whenever you want. Ask Claude to walk you through it — the files don't change.
