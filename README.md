<p align="center">
  <img src="sylvara_bg.png" width="180" style="border-radius: 50%;" alt="Sylvara"/>
</p>

<h1 align="center">Sylvara</h1>
<p align="center"><em>Stay rooted. Keep growing.</em></p>

<p align="center">
  <img src="https://img.shields.io/badge/python-3.11+-1D9E75?style=flat-square&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/discord.py-2.3+-5865F2?style=flat-square&logo=discord&logoColor=white"/>
  <img src="https://img.shields.io/badge/The%20Gardens-internal-1D9E75?style=flat-square"/>
</p>

---

Sylvara is a calm, advisory Discord bot built for **The Gardens** community.
She handles wellness tracking, productivity, a rich ticket system, and Twitch integration — all in one bot, separate from ~~__Cheru__~~.

---

## Features

| Pillar | Commands |
|--------|----------|
| **Wellness** | `/checkin` `/habits` `/burnout` `/breathe` |
| **Goals & Focus** | `/goal set` `/goal update` `/goal view` `/focus start` `/focus end` `/focus log` |
| **Productivity** | `/standup` `/review` `/remind me` `/remind list` `/remind cancel` |
| **Community** | `/pulse` `/accountability pair` `/accountability shoutout` |
| **Tickets** | `/ticket setup` `/ticket panel` `/ticket claim` `/ticket close` |
| **Twitch** | `/stream config` `/stream alert` `/stream clip` `/stream schedule` `/stream stats` `/stream milestone` |
| **Admin** | `/wellness setup` `/ticket setup` `/stream config` |

---

## Project Structure

```
sylvara/
├── bot.py                  # Entry point
├── requirements.txt
├── .env.example
├── index.html              # GitHub Pages landing page
├── cogs/
│   ├── tickets.py          # Ticket system — panel, claim, close, transfer, priority
│   ├── twitch.py           # Twitch alerts, clips, schedule, milestones
│   └── wellness.py         # Check-ins, habits, goals, focus, reminders
└── utils/
    ├── db.py               # Async SQLite helpers
    └── embeds.py           # Shared embed builders and colour constants
```

---

## Setup

### 1. Clone and install

```bash
git clone https://github.com/grxomen/sylvara
cd sylvara
pip install -r requirements.txt
```

### 2. Configure environment

```bash
cp .env.example .env
```

Edit `.env`:

```env
DISCORD_TOKEN=your_bot_token_here
DB_PATH=sylvara.db
TWITCH_CLIENT_ID=your_twitch_client_id
TWITCH_CLIENT_SECRET=your_twitch_client_secret
```

> **Discord token** — [discord.com/developers](https://discord.com/developers/applications) → New Application → Bot → Reset Token
>
> **Twitch credentials** — [dev.twitch.tv/console](https://dev.twitch.tv/console) → Register Your Application → set redirect to `http://localhost`

### 3. Run

```bash
python bot.py
```

Sylvara will sync slash commands on startup.

---

## First-time Discord setup

### Tickets

1. Run `/ticket setup` — set your support role, ticket category, and log channel
2. Go to your `#open-a-ticket` channel and run `/ticket panel`
3. The embed appears and persists across bot restarts

### Twitch

```
/stream config twitch_login:yourname alert_channel:#stream-alerts
```

Optional: add `clip_channel` and `milestone_channel` for separate routing.

### Wellness

```
/wellness setup checkin_channel:#daily-checkin hour:9
```

Posts a daily check-in prompt at 09:00 UTC.

---

## Ticket Lifecycle

```
User opens (category select)
  → Private channel created
  → Rich embed with Claim / Close / Transfer / Priority
  → Staff claims ticket
  → Priority updated (low / medium / urgent)
  → Ticket closed (reason modal)
  → Transcript saved to log channel
  → Channel deleted after 10s
```

---

## Reminder Formats

`/remind me` accepts natural time inputs:

| Input | Meaning |
|-------|---------|
| `30m` | 30 minutes from now |
| `2h`  | 2 hours from now |
| `1d`  | 1 day from now |
| `1d2h30m` | combined offset |
| `14:30` | specific UTC time today |

Repeat options: `none` · `daily` · `weekly`

---

## Companion Bot

Sylvara is a sibling bot to **[~~__Cheru__~~**, the garden economy bot for The Gardens.
They live side by side — Cheru handles the world, Sylvara keeps the people in it grounded.

---

<p align="center">
  <sub>Built for The Gardens · 2026</sub>
</p>
