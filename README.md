این را کامل کپی کن و جایگزین کل متن README در گیت‌هاب کن:

```markdown
# 🚀 YouTube Trend Analyzer & AI Strategy Bot

An asynchronous, production-ready Python framework designed to monitor YouTube video trends in real-time, extract viral metrics, analyze underlying content strategies using LLMs, and generate rich HTML summary cards directly to Telegram.

![Python Version](https://img.shields.io/badge/python-3.10%2B-blue.svg)
![Architecture](https://img.shields.io/badge/architecture-Asyncio%20%7C%20Pydantic%20%7C%20SQLite-green.svg)
![License](https://img.shields.io/badge/license-MIT-orange.svg)

---

## ✨ Key Features

- **⚡ Dual Scraping Engine:** Combines fast YouTube RSS feeds with targeted fallback queries using YouTube Data API v3.
- **🧠 Fault-Tolerant LLM Analysis:** Integrates Gemini/DeepSeek models to break down viral hooks, engagement sentiment, and content strategy recommendations.
- **🛡️ Robust JSON Extraction:** Features layered JSON parsers that extract valid strategy payloads even when LLM providers return messy or conversational responses.
- **📲 Telegram Rich Formatting:** Renders clean, highly actionable HTML analytical cards directly in designated Telegram channels.
- **💾 Local SQLite Caching:** Prevents re-analyzing processed videos and tracks historical view velocities.
- **🔒 Production Security:** Built-in proxy routing, automatic retry fallbacks, and environment variable protection.

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

---

## ⚙️ Quick Start Guide

**1. Clone the Repository**

```bash
git clone https://github.com/Sajadapp/Youtube-Trend-Analyzer.git
cd Youtube-Trend-Analyzer
```

**2. Set Up Virtual Environment & Dependencies**

```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

**3. Environment Configuration**

```bash
cp .env.example .env
```

*(Fill in your keys inside the .env file)*

**4. Run the Bot**

```bash
python main.py --mode once
```

---

## 📜 License

Distributed under the **MIT License**.

Developed with ❤️ by **[Sajad Kazemi](https://github.com/Sajadapp)**
```

مشکل اصلی متنت این بود: همه کاراکترها escape شده بودند (`\#`، `\*`، `\!`، `\---`). این معمولا وقتی پیش می‌آید که متن از یک رندر اشتباه کپی شده. نسخه بالا تمیزشده و تست‌شده است.
