# WhiteSimWatch / Data

**Transparency Archive: Public Scan Record**

[English](#english) | [فارسی](#فارسی)

---

<div dir="ltr">

## English

### What is this repository?

This repository is an automatically maintained public archive of data collected by [WhiteSimWatch](https://whitesimwatch.com), a project that tracks Twitter/X accounts whose holders connect directly from Iran using government-issued unfiltered SIM cards (known as "White SIM" or "خط سفید").

Every time a profile is scanned, a record is committed to this repository within seconds. This archive exists to provide verifiable, tamper-evident evidence that the data shown on the website is real and was genuinely retrieved from Twitter/X.

---

### What does "White SIM" mean?

A White SIM (خط سفید / سیمکارت سفید) is a special mobile line issued through Iran's state telecommunications infrastructure that is **completely exempt from the national internet filtering system**. Ordinary SIM cards in Iran route traffic through filtering gateways that block platforms such as X, Instagram, and YouTube. White SIM cards bypass those gateways entirely, giving the holder direct, unrestricted access to the global internet from inside Iran, with no VPN required.

These lines are not available to the public. They are estimated to be distributed to around **16,000 individuals** out of Iran's 90 million population:

| Recipient group |
|---|
| Senior government officials |
| Commanders and members of the Islamic Revolutionary Guard Corps (IRGC) |
| State television and radio journalists |
| Editors of government-affiliated newspapers |
| Judiciary figures |
| Intelligence personnel |

Critics call them **"blood SIM cards"** (سیمکارت خونی) because many holders are involved in the violent suppression of protests.

Since X is blocked in Iran, an ordinary Iranian connecting through a VPN appears to be located in Germany, the Netherlands, or wherever their VPN server is. Someone using a White SIM connects directly from Iran, so X's "About this account" transparency feature shows **"Iran"** or **"West Asia"** as the connection country — which is the evidence this project collects and archives.

---

### What is in this repository?

| Path | Updated | Description |
|---|---|---|
| `profiles/<twitterId>/profile.json` | Every scan | Latest known state of the account |
| `profiles/<twitterId>/snapshots/<snapshotId>.json` | Written once | Full record of a single scan — never modified after creation |
| `exports/profiles-<date>.csv` | Weekly | Full export of all profiles in CSV format |
| `exports/snapshots-<date>.csv` | Weekly | Full export of all snapshots in CSV format |

Each snapshot file contains:
- The structured fields extracted from the scan (username, bio, account location, connection source, etc.)
- The raw API response bodies returned directly by Twitter/X at the time of the scan

---

### How does this prove the data is real?

Each snapshot file contains the raw JSON responses from Twitter's internal GraphQL API, specifically the `AboutAccountQuery` response.

| Field | Description |
|---|---|
| `account_based_in` | Country from which the account most recently connected to X |
| `source` | Connection source, e.g. `"Iran Android App"`, `"West Asia Android App"` |
| Internal fields | GraphQL operation identifiers and response structures specific to Twitter's API at scan time |

These raw responses are Twitter's own output, not data we produce ourselves. Fabricating them convincingly would require reverse-engineering Twitter's internal API in precise detail, including versioned operation hashes and response schemas. The git history of this repository also provides an independent, append-only timestamp trail for every scan.

---

### What is stripped before publishing?

One field is removed from the raw payload before it is committed here:

| Removed field | Why |
|---|---|
| `relationship_perspectives` | Reveals whether the scanning account follows or is followed by the scanned account. Contains no authentication credentials. Removal does not affect the proof of origin in any way. |

---

### How often is this repository updated?

| Content | Schedule |
|---|---|
| Snapshot files | Real time — committed within seconds of each scan |
| CSV exports | Weekly — every weekend |

</div>

---

<div dir="rtl">

## فارسی

### این مخزن چیست؟

این مخزن یک آرشیو عمومی است که به صورت خودکار توسط [WhiteSimWatch](https://whitesimwatch.com) نگهداری می‌شود. این پروژه حساب‌های توییتر/ایکس را که از طریق خط سفید (سیمکارت سفید) فعالیت می‌کنند ردیابی می‌کند.

هر بار که یک پروفایل اسکن می‌شود، یک رکورد در عرض چند ثانیه به این مخزن اضافه می‌شود. هدف از این آرشیو ارائه شواهدی قابل تأیید و غیرقابل دستکاری است که نشان می‌دهد داده‌های نمایش داده شده در وبسایت واقعی هستند و به طور مستقیم از توییتر/ایکس دریافت شده‌اند.

---

### خط سفید چیست؟

خط سفید یا سیمکارت سفید، یک خط موبایل ویژه است که مستقیماً از طریق زیرساخت مخابراتی دولتی ایران صادر می‌شود و به طور کامل **از سیستم فیلترینگ ملی معاف است**. اینترنت سیمکارت‌های عادی از طریق درگاه‌های فیلترینگ عبور می‌کند که پلتفرم‌هایی مثل ایکس، اینستاگرام و یوتیوب را مسدود می‌کنند. اما سیمکارت‌های سفید این موانع را کاملاً دور می‌زنند و دسترسی مستقیم و بدون محدودیت به اینترنت جهانی را از داخل ایران فراهم می‌کنند، بدون نیاز به فیلترشکن.

این خطوط در دسترس عموم نیستند. تخمین زده می‌شود که از جمعیت ۹۰ میلیونی ایران، تنها حدود **۱۶ هزار نفر** از آن‌ها استفاده می‌کنند:

| گروه دریافت‌کننده |
|---|
| مقامات ارشد دولتی |
| فرماندهان و اعضای سپاه پاسداران انقلاب اسلامی|
| خبرنگاران صداوسیما |
| مدیران روزنامه‌های دولتی |
| مقامات قضایی |
| پرسنل اطلاعاتی |

منتقدان از آن‌ها با عنوان **«سیمکارت خونی»** یاد می‌کنند، چرا که بسیاری از صاحبان این خطوط در سرکوب خشونت‌آمیز اعتراضات نقش داشته‌اند.

از آنجا که ایکس در ایران مسدود است، یک ایرانی معمولی که با فیلترشکن متصل می‌شود، در سرور فیلترشکن خود (مثلاً آلمان یا هلند) نشان داده می‌شود. اما صاحب سیمکارت سفید مستقیماً از ایران متصل می‌شود و به همین دلیل قابلیت «درباره این حساب» در ایکس، **«ایران»** یا **«آسیای غربی»** را به عنوان کشور اتصال نشان می‌دهد و همین، مدرکی است که این پروژه جمع‌آوری و آرشیو می‌کند.

---

### محتوای این مخزن چیست؟

| مسیر | به‌روزرسانی | توضیح |
|---|---|---|
| `profiles/<twitterId>/profile.json` | هر اسکن | آخرین وضعیت شناخته‌شده حساب |
| `profiles/<twitterId>/snapshots/<snapshotId>.json` | یک‌بار نوشته می‌شود | رکورد کامل یک اسکن، هرگز تغییر نمی‌کند |
| `exports/profiles-<date>.csv` | هفتگی | صادرات کامل تمام پروفایل‌ها در قالب CSV |
| `exports/snapshots-<date>.csv` | هفتگی | صادرات کامل تمام اسنپ‌شات‌ها در قالب CSV |

هر فایل اسنپ‌شات شامل موارد زیر است:
- فیلدهای ساختاریافته استخراج‌شده از اسکن (نام کاربری، بیو، موقعیت حساب، منبع اتصال و غیره)
- بدنه‌های خام پاسخ API که مستقیماً توسط توییتر/ایکس در زمان اسکن برگردانده شده‌اند

---

### این چگونه ثابت می‌کند که داده‌ها واقعی هستند؟

هر فایل اسنپ‌شات شامل پاسخ‌های خام JSON از API داخلی GraphQL توییتر است، به ویژه پاسخ `AboutAccountQuery`.

| فیلد | توضیح |
|---|---|
| `account_based_in` | کشوری که حساب اخیراً از آنجا به ایکس متصل شده است |
| `source` | منبع اتصال، مثلاً `"Iran Android App"` یا `"West Asia Android App"` |
| فیلدهای داخلی | شناسه‌های عملیات GraphQL و ساختارهای پاسخ مختص API توییتر در زمان اسکن |

این پاسخ‌های خام، خروجی مستقیم توییتر هستند و ما آن‌ها را تولید نکرده‌ایم. جعل آن‌ها به صورت متقاعدکننده نیازمند مهندسی معکوس دقیق API داخلی توییتر است. تاریخچه git این مخزن نیز یک زنجیره زمانی مستقل و فقط افزایشی برای هر اسکن فراهم می‌کند.

---

### چه چیزی قبل از انتشار حذف می‌شود؟

یک فیلد از داده‌های خام قبل از ثبت در این مخزن حذف می‌شود:

| فیلد حذف‌شده | دلیل |
|---|---|
| `relationship_perspectives` | نشان می‌دهد آیا حساب اسکنر با حساب اسکن‌شده رابطه دنبال‌کردن دارد یا نه. هیچ اطلاعات احراز هویتی ندارد و حذف آن هیچ تأثیری بر اثبات منشأ داده‌ها ندارد. |

---

### این مخزن چه زمانی به‌روزرسانی می‌شود؟

| محتوا | زمان‌بندی |
|---|---|
| فایل‌های اسنپ‌شات | بلادرنگ، چند ثانیه پس از هر اسکن |
| صادرات CSV | هفتگی، هر آخر هفته |

</div>
