<!-- HEADER -->
<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=2,12,24&height=200&section=header&text=EchoBot&fontSize=72&fontColor=fff&animation=fadeIn&fontAlignY=38&desc=Telegram%20Echo%20Bot%20%C2%B7%20Built%20with%20Python&descAlignY=60&descColor=ffffff99" width="100%"/>

<br/>

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Telegram Bot API](https://img.shields.io/badge/Telegram%20Bot%20API-Latest-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)](https://core.telegram.org/bots/api)
[![python-telegram-bot](https://img.shields.io/badge/python--telegram--bot-v21%2B-blue?style=for-the-badge)](https://python-telegram-bot.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)
[![Code Style: Black](https://img.shields.io/badge/Code%20Style-Black-000000?style=for-the-badge)](https://github.com/psf/black)

<br/>

[![Stars](https://img.shields.io/github/stars/DragAditya/EchoBot?style=social)](https://github.com/DragAditya/EchoBot/stargazers)
[![Forks](https://img.shields.io/github/forks/DragAditya/EchoBot?style=social)](https://github.com/DragAditya/EchoBot/network/members)
[![Issues](https://img.shields.io/github/issues/DragAditya/EchoBot?color=red)](https://github.com/DragAditya/EchoBot/issues)
[![Last Commit](https://img.shields.io/github/last-commit/DragAditya/EchoBot)](https://github.com/DragAditya/EchoBot/commits/main)
[![Repo Size](https://img.shields.io/github/repo-size/DragAditya/EchoBot)](https://github.com/DragAditya/EchoBot)

<br/>

> **EchoBot** is a clean, minimal Telegram bot built in Python that echoes back every message a user sends. The perfect foundation and learning template for anyone starting out with the **Telegram Bot API** and `python-telegram-bot`. Zero bloat. Pure logic. Ready to extend.

<br/>

**[🤖 Try the Bot](https://t.me/YourBotUsername) · [📖 Docs](#-how-it-works) · [🚀 Deploy](#-deployment) · [🐛 Report Bug](https://github.com/DragAditya/EchoBot/issues) · [✨ Request Feature](https://github.com/DragAditya/EchoBot/issues)**

<br/>

</div>

---

## 📋 Table of Contents

<details>
<summary>Click to expand</summary>

- [✨ Features](#-features)
- [🛠 Tech Stack](#-tech-stack)
- [⚙️ How It Works](#️-how-it-works)
- [📦 Project Structure](#-project-structure)
- [🚀 Quick Start](#-quick-start)
- [🔧 Configuration](#-configuration)
- [☁️ Deployment](#️-deployment)
- [🗺 Roadmap](#-roadmap)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

</details>

---

## ✨ Features

| Feature | Description |
|---|---|
| 🔁 **Message Echo** | Instantly replies with the exact text the user sent |
| ⚡ **Async Architecture** | Built on `asyncio` — non-blocking, fast, scalable |
| 🛑 **Graceful Shutdown** | Handles `Ctrl+C` and OS signals cleanly |
| 📋 **Logging** | Built-in Python logging for debugging and monitoring |
| 🧩 **Extensible** | Clean structure — add commands and handlers in minutes |
| 🐍 **Pure Python** | No framework overhead, just the official PTB library |

---

## 🛠 Tech Stack

<div align="center">

| Layer | Technology | Version |
|---|---|---|
| **Language** | Python | 3.10+ |
| **Bot Framework** | python-telegram-bot | v21+ |
| **Async Runtime** | asyncio (stdlib) | — |
| **API** | Telegram Bot API | Latest |
| **Package Manager** | pip | — |

</div>

---

## ⚙️ How It Works

EchoBot uses the **polling** method to receive updates from Telegram and the `MessageHandler` to respond to any text message.

```
User sends message
       │
       ▼
Telegram Servers
       │
       ▼  (long polling)
   bot.py
       │
       ▼
 echo() handler
       │
       ▼
update.message.reply_text(text)
       │
       ▼
User receives their message back
```

### Core Handler

```python
async def echo(update: Update, context: ContextTypes.DEFAULT_TYPE) -> None:
    """Echo the user message back."""
    await update.message.reply_text(update.message.text)
```

That's it. Clean, minimal, correct.

---

## 📦 Project Structure

```
EchoBot/
│
├── 🤖 bot.py              # Main bot logic — handlers, startup, polling
├── 📋 requirements.txt    # Python dependencies
└── 📖 README.md           # You are here
```

---

## 🚀 Quick Start

### Prerequisites

- Python **3.10 or higher**
- A Telegram account
- A bot token from [@BotFather](https://t.me/BotFather)

### Step 1 — Get a Bot Token

```
1. Open Telegram → search @BotFather
2. Send /newbot
3. Follow the prompts → choose a name and username
4. Copy the token: 123456789:ABCdefGHIjklMNOpqrSTUvwxYZ
```

### Step 2 — Clone the Repo

```bash
git clone https://github.com/DragAditya/EchoBot.git
cd EchoBot
```

### Step 3 — Install Dependencies

```bash
# Create a virtual environment (recommended)
python -m venv venv

# Activate it
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install requirements
pip install -r requirements.txt
```

### Step 4 — Add Your Token

Open `bot.py` and replace the placeholder with your bot token:

```python
# bot.py
TOKEN = "YOUR_BOT_TOKEN_HERE"
```

> ⚠️ **Never commit your token to GitHub.** See [Configuration](#-configuration) for the `.env` approach.

### Step 5 — Run the Bot

```bash
python bot.py
```

You should see:
```
INFO - Application started
INFO - Listening for updates...
```

Open Telegram → find your bot → send any message → it echoes back. ✅

---

## 🔧 Configuration

### Using Environment Variables (Recommended)

Instead of hardcoding the token, use a `.env` file:

**1. Install `python-dotenv`:**
```bash
pip install python-dotenv
```

**2. Create a `.env` file:**
```env
BOT_TOKEN=123456789:ABCdefGHIjklMNOpqrSTUvwxYZ
```

**3. Update `bot.py`:**
```python
import os
from dotenv import load_dotenv

load_dotenv()
TOKEN = os.getenv("BOT_TOKEN")
```

**4. Add `.env` to `.gitignore`:**
```bash
echo ".env" >> .gitignore
```

> 🔐 Your token is now safe and never touches version control.

---

## ☁️ Deployment

### 🐳 Docker

```dockerfile
FROM python:3.11-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .

CMD ["python", "bot.py"]
```

```bash
# Build
docker build -t echobot .

# Run with token as env var
docker run -e BOT_TOKEN=your_token_here echobot
```

---

### 🚂 Railway (Free Tier)

```bash
# Install Railway CLI
npm install -g @railway/cli

# Login and deploy
railway login
railway init
railway up
```

Set `BOT_TOKEN` in Railway's environment variables dashboard. Done.

---

### 🟣 Heroku

```bash
# Login
heroku login
heroku create your-echobot

# Set token
heroku config:set BOT_TOKEN=your_token_here

# Deploy
git push heroku main
```

Add a `Procfile`:
```
worker: python bot.py
```

---

### 🖥️ VPS / Linux Server

```bash
# Clone and install
git clone https://github.com/DragAditya/EchoBot.git
cd EchoBot
pip install -r requirements.txt

# Run with screen (keeps it alive after SSH disconnect)
screen -S echobot
python bot.py
# Detach: Ctrl+A then D

# OR use systemd for production
```

**systemd service file** (`/etc/systemd/system/echobot.service`):
```ini
[Unit]
Description=EchoBot Telegram Bot
After=network.target

[Service]
Type=simple
User=ubuntu
WorkingDirectory=/home/ubuntu/EchoBot
ExecStart=/usr/bin/python3 bot.py
Restart=always
RestartSec=10
Environment=BOT_TOKEN=your_token_here

[Install]
WantedBy=multi-user.target
```

```bash
sudo systemctl daemon-reload
sudo systemctl enable echobot
sudo systemctl start echobot
sudo systemctl status echobot
```

---

### ☁️ Google Cloud Run / AWS Lambda

For serverless deployment, switch from polling to **webhooks**:

```python
# Instead of application.run_polling()
application.run_webhook(
    listen="0.0.0.0",
    port=8080,
    webhook_url="https://your-domain.com/webhook"
)
```

---

## 🗺 Roadmap

```
v1.0  ✅  Basic echo functionality
v1.1  🔲  /start and /help commands
v1.2  🔲  .env support built-in
v1.3  🔲  Dockerfile included
v1.4  🔲  Webhook mode support
v1.5  🔲  Inline keyboard example
v1.6  🔲  Message type detection (photo, sticker, voice, etc.)
v2.0  🔲  Full command handler scaffold
v2.1  🔲  GitHub Actions CI for automated testing
v2.2  🔲  One-click Railway / Render deploy button
```

Want a feature? [Open an issue →](https://github.com/DragAditya/EchoBot/issues/new)

---

## 🤝 Contributing

Contributions are welcome! This is a learning-focused project — PRs that improve clarity, add comments, or extend functionality are highly encouraged.

```bash
# 1. Fork the repo on GitHub

# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/EchoBot.git
cd EchoBot

# 3. Create a feature branch
git checkout -b feat/your-feature-name

# 4. Make your changes

# 5. Test locally
python bot.py

# 6. Commit using conventional commits
git commit -m "feat: add /help command"

# 7. Push and open a Pull Request
git push origin feat/your-feature-name
```

### Commit Convention

| Prefix | Use for |
|---|---|
| `feat:` | New feature |
| `fix:` | Bug fix |
| `docs:` | Documentation only |
| `refactor:` | Code restructure (no feature change) |
| `chore:` | Maintenance / dependency updates |

---

## 🔐 Security

- **Never** commit your `BOT_TOKEN` to any public repository
- Use `.env` files or environment variables for secrets
- Add `.env` to `.gitignore` before your first commit
- If you accidentally expose a token, regenerate it immediately via [@BotFather](https://t.me/BotFather) using `/revoke`

---

## 📚 Learn More

| Resource | Link |
|---|---|
| Telegram Bot API Docs | [core.telegram.org/bots/api](https://core.telegram.org/bots/api) |
| python-telegram-bot Docs | [docs.python-telegram-bot.org](https://docs.python-telegram-bot.org) |
| PTB Examples | [github.com/python-telegram-bot/python-telegram-bot/tree/master/examples](https://github.com/python-telegram-bot/python-telegram-bot/tree/master/examples) |
| BotFather | [@BotFather on Telegram](https://t.me/BotFather) |
| asyncio Docs | [docs.python.org/3/library/asyncio.html](https://docs.python.org/3/library/asyncio.html) |

---

## 📄 License

```
MIT License

Copyright (c) 2025 DragAditya

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

See [LICENSE](LICENSE) for full text.

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=2,12,24&height=100&section=footer" width="100%"/>

**Built with ❤️ by [DragAditya](https://github.com/DragAditya)**

⭐ Star this repo if EchoBot helped you get started with Telegram bots!

[![GitHub stars](https://img.shields.io/github/stars/DragAditya/EchoBot?style=social)](https://github.com/DragAditya/EchoBot)

</div>
