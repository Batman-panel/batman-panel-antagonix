<div align="center">

# 🦇 Batman Panel — Antagonix Edition

**A self-hosted subscription portal and link studio with protocol-specific configuration exports.**

[🇮🇷 فارسی](#فارسی) · [🇬🇧 English](#english)

[Repository](https://github.com/Batman-panel/batman-panel-antagonix) · [Report a bug](https://github.com/Batman-panel/batman-panel-antagonix/issues)

</div>

---

<a id="فارسی"></a>

# 🇮🇷 فارسی

## فهرست مطالب

- [معرفی](#معرفی)
- [قابلیت‌ها](#قابلیت‌ها)
- [فناوری‌ها و پیش‌نیازها](#فناوری‌ها-و-پیشنیازها)
- [نصب و اجرا](#نصب-و-اجرا)
- [پیکربندی محیط](#پیکربندی-محیط)
- [راهنمای استفاده](#راهنمای-استفاده)
- [پروتکل‌ها و فرمت‌های خروجی](#پروتکلها-و-فرمتهای-خروجی)
- [ذخیره‌سازی و ماندگاری داده‌ها](#ذخیرهسازی-و-ماندگاری-دادهها)
- [امنیت و حریم خصوصی](#امنیت-و-حریم-خصوصی)
- [عیب‌یابی](#عیبیابی)
- [ساختار پروژه](#ساختار-پروژه)
- [مشارکت](#مشارکت)
- [مجوز](#مجوز)

## معرفی

**Batman Panel — Antagonix Edition** یک برنامهٔ Node.js با رابط وب برای نمایش پورتال اشتراک، ساخت و مدیریت لینک‌های دسترسی و ارائهٔ خروجی‌های پیکربندی است. این پروژه یک پنل مستقل است؛ **جایگزین پنل مدیریت کانتینر یا API خصوصی Antagonix نیست** و به‌خودی‌خود منابع میزبانی را ایجاد یا افزایش نمی‌دهد.

> **وضعیت بررسی:** اطلاعات نصب و قابلیت‌های این راهنما بر اساس `package.json` و README موجود در شاخهٔ `main` تهیه شده‌اند. فایل `index.js` در GitHub حجمی حدود ۴٫۵۳ مگابایت دارد و رابط مرورگر امکان نمایش محتوای آن را نداد؛ بنابراین ممیزی کامل خط‌به‌خط کد، تأیید همهٔ مسیرهای API و اجرای عملی برنامه در این بررسی ممکن نشد. هرجا رفتار به پیکربندی میزبان وابسته است، این محدودیت صریحاً ذکر شده است.

## قابلیت‌ها

بر اساس مستندات فعلی پروژه:

- داشبورد مدیریتی با دسترسی‌های سریع، رویدادهای اخیر و نمایش اطلاعات منابع میزبان.
- پورتال اشتراک عمومی با خلاصهٔ سهمیه، حجم باقی‌مانده، میزان آپلود/دانلود و هشدار نزدیک‌شدن به انقضا یا پایان حجم.
- ارائهٔ لینک‌ها و خروجی‌های پیکربندی با امکان کپی و نمایش QR؛ همچنین دریافت مجموعهٔ پیکربندی‌ها به‌صورت TXT.
- بخش **Link Studio** برای جست‌وجوی کاربران، مشاهده و کپی لینک‌ها/پیکربندی‌ها، کپی گروهی، مخفی‌کردن دیداری لینک‌ها و پیش‌نمایش پورتال کاربر.
- تنظیم پروتکل‌های قابل ارائه و سقف تعداد خروجی‌ها از تنظیمات مدیر.
- تنظیم عنوان پروفایل و فاصلهٔ پیشنهادی به‌روزرسانی اشتراک.
- تعیین پیش‌فرض‌های ایجاد حساب، از جمله حجم، اعتبار زمانی، سقف سرعت و اتصال هم‌زمان؛ این مقادیر محدودیت‌های اعمال‌شده در برنامه‌اند و منابع واقعی میزبان را رزرو نمی‌کنند.
- چند پس‌زمینهٔ داخلی با حال‌وهوای تاریک و الهام‌گرفته از Gotham.

این فهرست بر پایهٔ README موجود است و به معنی آزمون عملی تمام قابلیت‌ها در این بررسی نیست.

## فناوری‌ها و پیش‌نیازها

| مورد | نیاز / توضیح |
|---|---|
| Node.js | نسخهٔ ۱۸ یا جدیدتر، طبق `package.json` |
| npm | برای نصب وابستگی‌ها و اجرای اسکریپت تعریف‌شده |
| وابستگی‌های مستقیم | `express` و `axios` |
| فضای ذخیره‌سازی پایدار | برای حفظ داده‌های برنامه پس از راه‌اندازی مجدد توصیه می‌شود |
| دسترسی شبکه | وابسته به قوانین و محدودیت‌های میزبان، پورت‌ها، DNS، TLS و فایروال |

## نصب و اجرا

پیش‌نیازها را روی محیطی نصب کنید که اجازهٔ اجرای برنامهٔ Node.js را می‌دهد. در ترمینال:

```bash
git clone https://github.com/Batman-panel/batman-panel-antagonix.git
cd batman-panel-antagonix
npm install
npm start
```

اسکریپت `start` در `package.json` برابر `node index.js` است. این مخزن در `package.json` اسکریپت `dev` یا اسکریپت ساخت جداگانه‌ای تعریف نکرده است.

در محیط میزبانی، پورت برنامه باید با متغیر `PORT` ارائه‌شده از سوی میزبان هماهنگ باشد. پس از اجرا، آدرس را از لاگ برنامه یا داشبورد میزبان بررسی کنید؛ چون کد اصلی در این بررسی به‌طور کامل قابل ممیزی نبود، شمارهٔ پورت پیش‌فرض یا مسیر دقیق صفحات را حدس نمی‌زنیم.

## پیکربندی محیط

مقادیر زیر در README موجود پروژه ذکر شده‌اند. مقدارهای محرمانه را در مخزن، اسکرین‌شات عمومی یا Issue منتشر نکنید.

| متغیر | کاربرد مستندشده | نکته |
|---|---|---|
| `PORT` | پورت HTTP برنامه | در محیط ابری معمولاً میزبان مقدار آن را تعیین می‌کند. |
| `BK_DATA_DIR` | مسیر پوشهٔ دادهٔ برنامه | آن را روی دیسک/Volume پایدار قرار دهید. |
| `PANEL_SETUP_KEY` | کلید راه‌اندازی اولیه | برای استقرار عمومی یک مقدار تصادفی و قوی انتخاب کنید و فقط در فرم راه‌اندازی اولیه وارد کنید. |
| `HOST_PANEL_URL` | نشانی پنل میزبان برای پیوندهای مربوط | نشانی واقعی استقرار خود را تنظیم کنید؛ مقدار پیش‌فرض مستندشده، صفحهٔ ورود عمومی Antagonix است و لزوماً پنل اختصاصی شما نیست. |
| `ENABLE_XHTTP` | فعال‌سازی گزینهٔ `VLESS-XHTTP` | طبق README فقط با مقدار `true` و در صورت فراهم‌بودن وابستگی‌ها/مجوزهای میزبان قابل استفاده است. |

README فعلی به فایل `.env.example` اشاره می‌کند، اما این فایل در شاخهٔ عمومی `main` با مسیر مورد بررسی پیدا نشد. همچنین پروژه وابستگی `dotenv` را در `package.json` اعلام نکرده است؛ بنابراین فرض نکنید فایل `.env` به‌صورت خودکار خوانده می‌شود. متغیرها را در بخش Environment/Variables میزبان تعریف کنید، مگر اینکه کد یا محیط اجرایی شما روش دیگری را صریحاً پیاده‌سازی کرده باشد.

مقادیر نمایشی CPU/RAM/دیسک که در README قبلی ذکر شده‌اند، مقادیر قابل تنظیم برای نمایش‌اند و به معنی تخصیص واقعی منابع توسط برنامه نیستند.

## راهنمای استفاده

1. برنامه را روی میزبانی اجرا کنید که قوانین آن اجرای پردازه‌ها و دسترسی شبکهٔ موردنیاز را مجاز می‌داند.
2. برای راه‌اندازی نخستین‌بار، `PANEL_SETUP_KEY` را در تنظیمات محیط قرار دهید و از مسیر راه‌اندازی اولیهٔ برنامه استفاده کنید.
3. پس از ورود مدیریتی، تنظیمات کاربران، پیش‌فرض‌های حساب و پروتکل‌های قابل ارائه را بررسی کنید.
4. برای یافتن و مدیریت لینک‌های کاربران از بخش Link Studio استفاده کنید. لینک‌ها و QRها ممکن است اطلاعات حساس دسترسی داشته باشند؛ آن‌ها را عمومی نکنید.
5. در پورتال اشتراک، فرمت مناسب کلاینت مقصد را انتخاب کنید. اگر یک فرمت سازگار همهٔ پروتکل‌ها را نشان نمی‌دهد، از خروجی Full/Raw و کلاینت سازگار استفاده کنید.
6. خروجی تولیدشده به معنی دسترس‌پذیری واقعی تونل از اینترنت نیست؛ اتصال را با کلاینت مقصد و از شبکهٔ واقعی خود آزمایش کنید.

نام دقیق دکمه‌ها و مسیر صفحات ممکن است با تغییر نسخه فرق کند؛ به دلیل محدودیت دسترسی به کد حجیم، راهنمای تصویری یا مسیرهای دقیق رابط در این سند درج نشده است.

## پروتکل‌ها و فرمت‌های خروجی

README موجود، این پروتکل‌ها را به‌عنوان موارد پیاده‌سازی‌شده یا قابل ارائه نام می‌برد:

- `VLESS-TCP`
- `VMess-WS`
- `Trojan-TCP`
- `ShadowTLS-VLESS`
- `VLESS-XHTTP` — گزینه‌ای مشروط که طبق مستندات به `ENABLE_XHTTP=true`، در دسترس بودن باینری Xray و اجازهٔ میزبان وابسته است.

فرمت‌های خروجی ذکرشده:

- لینک اصلی اشتراک
- `v2ray`
- `Full`
- `Raw`
- `Clash Meta`
- `Sing-box`
- فایل متنی `TXT` برای دریافت مجموعهٔ کانفیگ‌ها

خروجی‌های سازگار با یک کلاینت ممکن است زیرمجموعه‌ای از پروتکل‌های انتخاب‌شده باشند. برای `VLESS-XHTTP` از خروجی Full/Raw و کلاینت سازگار با Xray استفاده کنید؛ سازگاری خروجی‌های دیگر تضمین نشده است. فعال‌کردن یک پروتکل در تنظیمات، لزوماً هسته یا Listener شبکه را روشن نمی‌کند.

**محدودیت مهم:** دامنه و DNS، گواهی TLS، پورت‌های قابل دسترسی، فایروال، پشتیبانی TCP/UDP و سیاست‌های میزبان بر اتصال واقعی اثر دارند. اگر میزبان فقط یک پورت TCP وب بدهد یا UDP را مسدود کند، همهٔ روش‌ها قابل استفاده نخواهند بود. پروژه طبق README موجود به API مدیریتی خصوصی Antagonix متصل نیست و ساخت، حذف، تمدید یا توقف کانتینرهای Antagonix را انجام نمی‌دهد.

## ذخیره‌سازی و ماندگاری داده‌ها

- تنظیمات مدیریتی در فایل `panel-settings.json` داخل مسیر `BK_DATA_DIR` ذخیره می‌شوند.
- برای باقی‌ماندن اطلاعات پس از راه‌اندازی مجدد یا جایگزینی نمونهٔ برنامه، `BK_DATA_DIR` را به فضای ذخیره‌سازی پایدار متصل کنید.
- اگر مسیر داده در فایل‌سیستم موقت میزبان باشد، حذف یا بازسازی نمونه می‌تواند باعث از دست رفتن داده‌ها شود.
- پیش از به‌روزرسانی یا تغییر زیرساخت، از پوشهٔ داده نسخهٔ پشتیبان امن بگیرید.
- نمایش «داده‌های برنامه روی دیسک» به اندازهٔ پوشهٔ داده اشاره دارد و الزاماً مصرف کل دیسک میزبان نیست.

## امنیت و حریم خصوصی

- از `PANEL_SETUP_KEY` تصادفی، طولانی و منحصربه‌فرد استفاده کنید؛ آن را در کد یا مخزن عمومی قرار ندهید.
- پنل مدیریتی را در صورت امکان پشت کنترل دسترسی و HTTPS معتبر قرار دهید و دسترسی مدیریتی را به افراد مورد اعتماد محدود کنید.
- مجوزهای فایل‌های داده و نسخه‌های پشتیبان را محدود کنید؛ مسیر داده نباید برای کاربران وب قابل دانلود مستقیم باشد.
- لینک اشتراک، UUID، کلیدها، رمزها و کانفیگ‌ها را اطلاعات حساس فرض کنید. پیش از انتشار Issue یا لاگ، این داده‌ها را حذف یا ماسک کنید.
- کلیدها و رمزها را در لاگ‌ها، تصاویر صفحه یا پیام‌های پشتیبانی قرار ندهید. اگر افشا شدند، آن‌ها را تعویض کنید.
- از به‌روز بودن Node.js و وابستگی‌ها مطمئن شوید و فقط از میزبان‌هایی استفاده کنید که سیاست‌هایشان با اجرای این برنامه سازگار است.
- پنهان‌کردن دیداری لینک در Link Studio صرفاً یک قابلیت حریم دیداری است؛ آن را رمزنگاری یا محافظت دسترسی در نظر نگیرید.
- آمار CPU/RAM ممکن است از cgroups خوانده شود یا به‌صورت تخمینی نمایش داده شود؛ این ارقام را جایگزین آمار رسمی میزبان نکنید.

## عیب‌یابی

| نشانه | بررسی پیشنهادی |
|---|---|
| برنامه شروع نمی‌شود | نسخهٔ Node.js را با `node --version` بررسی کنید؛ سپس `npm install` را اجرا و خطای کامل ترمینال را بررسی کنید. |
| خطای پورت یا برنامه در دسترس نیست | مطمئن شوید برنامه از `PORT` مورد انتظار میزبان استفاده می‌کند و میزبان همان پورت را به سرویس متصل کرده است. |
| تنظیمات پس از ری‌استارت از بین می‌روند | مقدار `BK_DATA_DIR` و اتصال Volume پایدار را بررسی کنید. |
| گزینهٔ `VLESS-XHTTP` نمایش داده نمی‌شود | `ENABLE_XHTTP=true`، در دسترس بودن باینری Xray و اجازهٔ میزبان برای اجرای آن را بررسی کنید. |
| لینک ساخته شده اما اتصال برقرار نیست | DNS، دامنه، TLS، فایروال، پورت‌ها، محدودیت TCP/UDP و سازگاری کلاینت را بررسی کنید. ساخته‌شدن لینک اثبات اتصال موفق نیست. |
| یک پروتکل در خروجی کلاینت وجود ندارد | محدودیت فرمت و کلاینت را بررسی کنید؛ Full/Raw ممکن است گزینه‌های بیشتری از خروجی‌های سازگار داشته باشد. |
| آمار منابع با داشبورد میزبان فرق دارد | اطلاعات cgroups ممکن است در دسترس نباشد و برنامه در آن حالت تخمین نشان دهد. |
| مصرف حافظه بالا است یا پردازهٔ جانبی اجرا نمی‌شود | منابع واقعی میزبان و سیاست اجرای باینری‌ها را بررسی کنید؛ محیط‌های کم‌حافظه ممکن است برای چند پردازه کافی نباشند. |

موارد جدول، راهنمای بررسی احتمال‌ها هستند و به معنی تأیید وجود باگ در همهٔ استقرارها نیستند.

## ساختار پروژه

```text
batman-panel-antagonix/
├── index.js          # برنامهٔ اصلی؛ رابط و منطق در یک فایل بزرگ قرار دارند
├── package.json      # فراداده، وابستگی‌ها و دستور start
├── README.md         # مستندات انگلیسی/دوزبانه
└── assets/           # منابع تصویری رابط؛ از جمله پس‌زمینه‌ها
```

ساختار بالا خلاصه‌ای از فایل‌های شناخته‌شده در مستندات است، نه فهرست کامل و تأییدشدهٔ همهٔ فایل‌های مخزن. README موجود به `assets/bg6.jpg`، `assets/bg7.jpg` و `assets/bg8.jpg` اشاره می‌کند. وجود فایل‌های دیگر در پوشهٔ `assets` در این بررسی به‌طور کامل ممیزی نشد.

## مشارکت

برای گزارش باگ یا پیشنهاد بهبود، از [Issues مخزن](https://github.com/Batman-panel/batman-panel-antagonix/issues) استفاده کنید. در گزارش خود این موارد را بیاورید:

- نسخهٔ Node.js و سیستم/میزبان اجرا
- مراحل بازتولید خطا و رفتار مورد انتظار
- پیام خطا با حذف رمزها، لینک‌های اشتراک و سایر اطلاعات حساس
- تغییرات محیطی مرتبط، بدون درج مقادیر محرمانه

برای تغییرات کد، یک شاخهٔ جداگانه بسازید و Pull Request کوچک و مشخص ارسال کنید. پیش از ارسال، مطمئن شوید هیچ کلید، رمز، شناسهٔ کاربر یا لینک دسترسی در تغییرات قرار نگرفته باشد.

## مجوز

فیلد `license` در `package.json` مقدار `MIT` را اعلام می‌کند. با این حال، فایل مستقل `LICENSE` در مسیر ریشهٔ شاخهٔ `main` در این بررسی پیدا نشد. پیش از انتشار رسمی، وجود فایل مجوز و تطابق متن آن با مجوز اعلام‌شده را در مخزن بررسی کنید. این مستندات جایگزین مشاورهٔ حقوقی نیستند.

---

<div align="center">

**🦇 Batman Panel — Antagonix Edition**  
*Built for clarity. Operate responsibly. Protect your secrets.*

</div>

---

<a id="english"></a>

# 🇬🇧 English

## Table of contents

- [Overview](#overview)
- [Features](#features)
- [Technology and requirements](#technology-and-requirements)
- [Installation and startup](#installation-and-startup)
- [Environment configuration](#environment-configuration)
- [Using the panel](#using-the-panel)
- [Protocols and export formats](#protocols-and-export-formats)
- [Storage and persistence](#storage-and-persistence)
- [Security and privacy](#security-and-privacy)
- [Troubleshooting](#troubleshooting)
- [Project structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

## Overview

**Batman Panel — Antagonix Edition** is a Node.js web application for presenting a subscription portal, organizing access links, and serving configuration exports. It is a standalone panel; **it is not a replacement for Antagonix's container-management panel or private API**, and it does not create or increase hosting resources by itself.

> **Review status:** Installation details and feature descriptions in this guide are based on `package.json` and the existing README on the `main` branch. GitHub reports that `index.js` is approximately 4.53 MB, and the browser interface would not display its contents. A complete line-by-line code audit, verification of every API route, and a live application test were therefore not possible in this review. Host-dependent behavior is described with that limitation in mind.

## Features

According to the existing project documentation:

- An administrative dashboard with quick links, recent events, and host-resource information.
- A public subscription portal showing quota summaries, remaining traffic, upload/download usage, and warnings for near-expiry or exhausted quota.
- Configuration links and exports with copy and QR options, plus a TXT download of the configuration collection.
- **Link Studio** for searching users, viewing and copying links/configurations, bulk copying, visually masking links, and previewing a user's portal.
- Administrative controls for available protocols and the maximum number of generated outputs.
- Profile-title and suggested subscription-update interval settings.
- Defaults for account creation, including traffic, validity, speed limit, and concurrent connections. These are application-level limits; they do not reserve actual host resources.
- Several built-in dark, Gotham-inspired backgrounds.

This list reflects the existing README and does not mean every feature was exercised during this review.

## Technology and requirements

| Item | Requirement / note |
|---|---|
| Node.js | Version 18 or newer, according to `package.json` |
| npm | Used to install dependencies and run the defined script |
| Direct dependencies | `express` and `axios` |
| Persistent storage | Recommended to retain application data across restarts |
| Network access | Depends on host policies, ports, DNS, TLS, and firewall rules |

## Installation and startup

Use a host that permits the required Node.js runtime. In a terminal:

```bash
git clone https://github.com/Batman-panel/batman-panel-antagonix.git
cd batman-panel-antagonix
npm install
npm start
```

The `start` script in `package.json` is `node index.js`. The repository's `package.json` does not define a `dev` script or a separate build script.

In a hosting environment, align the application's port with the host-provided `PORT` variable. Check the application logs or hosting dashboard for the actual address. Since the large main source file could not be fully audited here, this guide does not guess a default port or exact page routes.

## Environment configuration

The variables below are named in the existing project README. Never publish secret values in the repository, public screenshots, or Issues.

| Variable | Documented purpose | Note |
|---|---|---|
| `PORT` | Application HTTP port | Cloud hosts commonly set this value automatically. |
| `BK_DATA_DIR` | Application data directory | Point it to persistent disk or a persistent volume. |
| `PANEL_SETUP_KEY` | Initial setup key | Set a strong random value for public deployments and enter it only in the initial setup form. |
| `HOST_PANEL_URL` | Host-panel URL used by related links | Set it to your actual deployment URL. The documented default is the public Antagonix login page, not necessarily your own instance. |
| `ENABLE_XHTTP` | Enables the `VLESS-XHTTP` option | According to the README, the option depends on `ENABLE_XHTTP=true`, an available Xray binary, and host permission. |

The existing README refers to `.env.example`, but that file was not found at the referenced path in the public `main` branch during this review. The project also does not declare `dotenv` in `package.json`; do not assume a `.env` file is automatically loaded. Define variables in your host's Environment/Variables settings unless your code or runtime explicitly implements another method.

CPU/RAM/disk display defaults mentioned in the previous README are configurable display values; they do not represent resources allocated by the application.

## Using the panel

1. Run the application on a host whose policies permit the required processes and network access.
2. For first-time setup, define `PANEL_SETUP_KEY` in the environment and use the application's initial setup flow.
3. After administrative sign-in, review user settings, account defaults, and the protocols made available for export.
4. Use Link Studio to find and manage users' links. Links and QR codes may contain sensitive access information; do not share them publicly.
5. In the subscription portal, choose an export compatible with the target client. If a compatible format omits selected protocols, use Full/Raw output with a compatible client.
6. A generated export does not prove that a tunnel is reachable from the public internet. Test it with the intended client from the actual network where it will be used.

Exact button labels and page routes may change between versions. Because the large source file could not be fully inspected, this document does not provide unverified UI screenshots or exact route names.

## Protocols and export formats

The existing README names the following as implemented or available for output:

- `VLESS-TCP`
- `VMess-WS`
- `Trojan-TCP`
- `ShadowTLS-VLESS`
- `VLESS-XHTTP` — conditional; according to the documentation it requires `ENABLE_XHTTP=true`, an available Xray binary, and host permission.

Documented export formats include:

- Main subscription link
- `v2ray`
- `Full`
- `Raw`
- `Clash Meta`
- `Sing-box`
- `TXT` download for the configuration collection

Client-compatible formats may include only a subset of the selected protocols. For `VLESS-XHTTP`, use Full/Raw output with an Xray-compatible client; support in other exports is not guaranteed. Enabling a protocol in settings does not necessarily start its core process or network listener.

**Important limitation:** Actual connectivity depends on domain and DNS configuration, TLS certificates, reachable ports, firewall rules, TCP/UDP support, and host policy. If the host only provides a web TCP port or blocks UDP, not every method will be reachable. According to the existing README, this project does not connect to Antagonix's private management API and does not create, delete, renew, or stop Antagonix containers.

## Storage and persistence

- Administrative settings are stored in `panel-settings.json` inside `BK_DATA_DIR`.
- To retain data across restarts or instance replacement, mount `BK_DATA_DIR` on persistent storage.
- If the data directory is on an ephemeral filesystem, deleting or recreating the instance may cause data loss.
- Back up the data directory securely before upgrades or infrastructure changes.
- The displayed “application data on disk” value refers to the application data directory; it is not necessarily the host's total disk usage.

## Security and privacy

- Use a long, random, unique `PANEL_SETUP_KEY`; never commit it to a public repository.
- Where possible, place the administrative panel behind access controls and valid HTTPS, and limit administrative access to trusted people.
- Restrict permissions on data files and backups. Do not make the data directory directly downloadable through the web server.
- Treat subscription URLs, UUIDs, keys, passwords, and configurations as sensitive credentials. Remove or mask them before publishing Issues or logs.
- Do not include secrets in logs, screenshots, or support messages. Rotate exposed credentials.
- Keep Node.js and dependencies updated, and use only hosting environments whose policies permit the application's behavior.
- Link masking in Link Studio is a visual privacy feature, not encryption or access control.
- CPU/RAM metrics may come from cgroups or be estimates; they are not a substitute for the host's official metrics.

## Troubleshooting

| Symptom | Suggested checks |
|---|---|
| The application does not start | Check Node.js with `node --version`, run `npm install`, and inspect the full terminal error. |
| Port error or unreachable application | Confirm the application uses the host's expected `PORT` and that the host routes that port to the service. |
| Settings disappear after restart | Check `BK_DATA_DIR` and the persistent-volume mount. |
| `VLESS-XHTTP` is not shown | Check `ENABLE_XHTTP=true`, Xray binary availability, and whether the host permits it. |
| A generated link does not connect | Check DNS, domain, TLS, firewall, ports, TCP/UDP restrictions, and client compatibility. Link generation is not proof of connectivity. |
| A protocol is missing from a client export | Check the export format and client limitations; Full/Raw may expose more options than compatibility-focused exports. |
| Resource metrics differ from the host dashboard | cgroup data may be unavailable, in which case the application may display estimates. |
| High memory use or a side process will not start | Check actual host resources and binary-execution policies; low-memory environments may not support several processes simultaneously. |

These are diagnostic suggestions, not claims that each issue is a confirmed bug in every deployment.

## Project structure

```text
batman-panel-antagonix/
├── index.js          # Main application; UI and logic are embedded in one large file
├── package.json      # Metadata, dependencies, and start command
├── README.md         # English/bilingual documentation
└── assets/           # UI image assets, including backgrounds
```

This is a summary of files identified in the available documentation, not a complete, verified inventory of the repository. The existing README mentions `assets/bg6.jpg`, `assets/bg7.jpg`, and `assets/bg8.jpg`. Other files in `assets` were not fully audited during this review.

## Contributing

Use the repository's [Issues page](https://github.com/Batman-panel/batman-panel-antagonix/issues) to report bugs or suggest improvements. Include:

- Node.js version and runtime/hosting environment
- Reproduction steps and expected behavior
- Error messages with passwords, subscription URLs, and other sensitive data removed
- Relevant environment-variable names, but never secret values

For code changes, create a separate branch and submit a focused Pull Request. Check that no keys, passwords, user identifiers, or access links are included in the diff.

## License

The `license` field in `package.json` declares `MIT`. However, a standalone `LICENSE` file was not found at the repository root on the `main` branch during this review. Before publishing, verify that the license file exists and that its text matches the declared license. This documentation is not legal advice.

---

<div align="center">

**🦇 Batman Panel — Antagonix Edition**  
*Built for clarity. Operate responsibly. Protect your secrets.*

</div>
