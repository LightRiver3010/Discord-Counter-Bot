<div align="center">

# Discord Counter Bot

**Count higher. Earn roles. Take the leaderboard.**

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![discord.py](https://img.shields.io/badge/discord.py-5865F2?style=for-the-badge&logo=discord&logoColor=white)
![Async IO](https://img.shields.io/badge/Async_IO-0F766E?style=for-the-badge)

A Python Discord bot that turns counting into a competitive server mini-game, with individual scores, live leaderboards, and achievement roles.

[Features](#features) · [Commands](#commands) · [Tech Stack](#tech-stack) · [Getting Started](#getting-started)

</div>

## Features

- **Individual counting streaks:** Each player posts `1, 2, 3, …` in `#bot-counting-channel`. An incorrect number resets that player's score; nonnumeric messages are ignored.
- **Server-specific leaderboards:** Track scores independently for each server, display the top three players, and announce changes in the lead.
- **Automatic achievements:** Award Discord roles as players reach counting milestones.
- **Opt-in mentions:** Let players choose whether they are mentioned when someone takes their lead.

| Score milestone | Achievement role |
| --- | --- |
| 10 | Amateur Counter |
| 50 | Intermediate Counter |
| 100 | Advanced Counter |
| 250 | Pro Counter |
| 3,010 | Master Counter |

## Commands

| Command | Action |
| --- | --- |
| `!score` / `!score @member` | Check your score or another player's. |
| `!leaderboard` | Show the server's top three scorers. |
| `!rules` | Display the game rules. |
| `!helpme` | List commands and descriptions. |
| `!pingrole` / `!nopingrole` | Enable or disable mentions when your lead is overtaken. |

## Tech Stack

| Technology | Implementation |
| --- | --- |
| **Python** | Game logic, input validation, dictionary-based state management, and score sorting. |
| **discord.py / Discord API** | Event-driven architecture, asynchronous `async`/`await` handlers, command routing, and role management. |
| **python-dotenv** | Load the bot token from environment configuration. |
| **Python logging** | Write Discord debug logs to `discord.log`. |

## Getting Started

1. Clone the repository and install dependencies in an activated Python virtual environment:

   ```bash
   git clone https://github.com/LightRiver3010/Discord-Counter-Bot.git
   cd Discord-Counter-Bot
   python -m pip install -r requirements.txt
   ```

2. Create a bot in the [Discord Developer Portal](https://discord.com/developers/applications). Enable **Message Content Intent** and **Server Members Intent**. Invite it with **View Channels**, **Send Messages**, and **Manage Roles** permissions.

3. Create `.env` alongside `main.py`:

   ```dotenv
   DISCORD_TOKEN2=your_bot_token_here
   ```

   Keep the token private; `.env` is already excluded by `.gitignore`.

4. Create `#bot-counting-channel` and place the bot's role above the achievement roles and `Bot Pings`. These roles are created when the running bot joins a server; if it was invited while offline, create the six roles manually using the exact names above and `Bot Pings`.

5. Start the bot, then send `1` in the counting channel:

   ```bash
   python main.py
   ```

> **Current scope:** Scores live in memory and reset when the process restarts. Use the bot in server text channels; direct messages are not supported by the current handlers.
