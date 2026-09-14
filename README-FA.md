# 🚀 تحلیل‌گر ترند یوتیوب و بات استراتژی هوش مصنوعی

فریم‌ورک ناهمگام (Async) پایتون برای رصد لحظه‌ای ترندهای یوتیوب، استخراج متریک‌های وایرال، تحلیل استراتژی محتوا با LLM و ارسال کارت خلاصه HTML به تلگرام.

> 🇬🇧 English version: [README.md](./README.md)

---

## ✨ قابلیت‌ها

- **⚡ موتور دوگانه اسکرپ:** فید سریع RSS یوتیوب + fallback با YouTube Data API v3.
- **🧠 تحلیل LLM مقاوم به خطا:** تحلیل هوک وایرال، سنتیمنت و پیشنهاد استراتژی با Gemini / DeepSeek.
- **🛡️ استخراج JSON مقاوم:** پارس چندلایه که از پاسخ‌های به‌هم‌ریخته LLM هم payload سالم بیرون می‌کشد.
- **📲 قالب‌بندی غنی تلگرام:** کارت تحلیلی HTML تمیز + ربات long-polling با رابط فارسی.
- **💾 کش SQLite محلی:** جلوگیری از تحلیل تکراری ویدیوها و ثبت سرعت رشد بازدید.
- **🔒 امنیت:** پروکسی، retry خودکار و نگهداری کلیدها فقط در `.env` (هرگز کامیت نمی‌شود).

---

## 🏗️ معماری

```text
[ YouTube RSS / API ] ──► [ اسکرپر ترند ] ──► [ کش SQLite ]
                                │
                                ▼
                       [ موتور LLM ] ──► (Gemini / DeepSeek)
                                │
                                ▼
                        [ اعتبارسنج Pydantic ]
                                │
                                ▼
                      [ ارسال کارت به تلگرام ]
```

مرجع کامل: [`ARCHITECTURE.md`](./ARCHITECTURE.md)

---

## ⚙️ شروع سریع

**۱. کلون کردن ریپو**

```bash
git clone https://github.com/Sajadapp/Youtube-Trend-Analyzer.git
cd Youtube-Trend-Analyzer
```

**۲. محیط مجازی و نصب وابستگی‌ها**

```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

**۳. تنظیم متغیرهای محیطی**

```bash
copy .env.example .env
```

حداقل این‌ها را پر کنید (لیست کامل در `.env.example`):

```env
YOUTUBE_API_KEY=your_youtube_api_key_here
LLM_PROVIDER=gemini
GEMINI_API_KEYS=your_gemini_or_gapgpt_api_key_here
TELEGRAM_BOT_TOKEN=your_telegram_bot_token_here
TELEGRAM_CHAT_ID=your_telegram_chat_id_here
```

> 🔐 فایل‌های `.env`، دیتابیس‌ها (`*.db`)، کوکی‌ها و فایل‌های `api key` را هرگز کامیت نکنید — این‌ها از قبل در `.gitignore` هستند.

**۴. اجرای بات**

```bash
python main.py --mode once
```

برای اجرای مداوم (پایش دوره‌ای) از `--mode scheduled` استفاده کنید.

---

## 📜 لایسنس

تحت لایسنس **MIT** منتشر شده است.

توسعه‌دهنده: **[Sajad Kazemi](https://github.com/Sajadapp)**
