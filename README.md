# 🚀 YouTube Trend Analyzer & AI Strategy Bot

An asynchronous, production-ready Python framework that monitors YouTube video trends in real-time, extracts viral metrics, analyzes content strategy with LLMs, and sends rich HTML summary cards to Telegram.

![Python Version](https://img.shields.io/badge/python-3.11%2B-blue.svg)
![Architecture](https://img.shields.io/badge/architecture-Asyncio%20%7C%20Pydantic%20%7C%20SQLite-green.svg)
![License](https://img.shields.io/badge/license-MIT-orange.svg)

---

## ✨ Key Features

- **⚡ Dual Scraping Engine:** Fast YouTube RSS feeds with targeted fallback via YouTube Data API v3.
- **🧠 Fault-Tolerant LLM Analysis:** Gemini / DeepSeek analysis of viral hooks, sentiment, and content strategy.
- **🛡️ Robust JSON Extraction:** Layered parsers that recover valid payloads from messy LLM responses.
- **📲 Telegram Rich Formatting:** Clean, actionable HTML analytical cards + long-polling bot with Persian UI.
- **💾 Local SQLite Caching:** Skips already-processed videos, tracks view velocity and quota state.
- **🔒 Production Security:** Proxy routing, retries, and secrets kept in `.env` (never committed).

---

## 🏗️ System Architecture

```text
[ YouTube RSS / API ] ──► [ Trend Scraper ] ──► [ SQLite Cache ]
                                │
                                ▼
                       [ LLM Engine ] ──► (Gemini / DeepSeek)
                                │
                                ▼
                     [ Pydantic Validator ]
                                │
                                ▼
                   [ Telegram Card Notifier ]
```

Full reference: [`ARCHITECTURE.md`](./ARCHITECTURE.md)

---

## 📁 Project Layout

```text
main.py               # async entry point (--mode once | scheduled)
config/               # pydantic-settings (RunMode, poll interval, keys)
core/                 # cli, logging, shutdown, services
scrapers/             # RSS + YouTube Data API clients
processors/           # per-video pipeline + trend analyst
services/llm/         # engine, prompts, schemas, JSON parser
services/notifier/    # Telegram client + card formatter
services/telegram/    # long-polling bot, commands, menus
dashboard/            # Streamlit dashboard (isolated service)
data/                 # SQLite DB, quota state (local only, git-ignored)
```

---

## ⚙️ Quick Start

**1. Clone the repository**

```bash
git clone https://github.com/Sajadapp/Youtube-Trend-Analyzer.git
cd Youtube-Trend-Analyzer
```

**2. Set up virtual environment & dependencies**

```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

**3. Configure environment**

```bash
copy .env.example .env
```

Fill in at minimum (see `.env.example` for the full list):

```env
YOUTUBE_API_KEY=your_youtube_api_key_here
LLM_PROVIDER=gemini
GEMINI_API_KEYS=your_gemini_or_gapgpt_api_key_here
TELEGRAM_BOT_TOKEN=your_telegram_bot_token_here
TELEGRAM_CHAT_ID=your_telegram_chat_id_here
```

> 🔐 Never commit `.env`, `*.db`, cookies, or `api key *.txt` files. They are already git-ignored.

**4. Run the bot**

```bash
python main.py --mode once
```

Use `--mode scheduled` for the continuous polling loop.

---

## 📜 License

Distributed under the **MIT License**.

Developed with ❤️ by **[Sajad Kazemi](https://github.com/Sajadapp)**
