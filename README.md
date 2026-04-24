# WhiteSimWatch / Data

**Transparency Archive: Public Scan Record**

[English](#english) | [فارسی](#فارسی)

---

## English

### What is this repository?

This repository is an automatically maintained public archive of data collected by [WhiteSimWatch](https://whitesimwatch.com), a project that tracks Twitter/X accounts whose holders connect directly from Iran using government-issued unfiltered SIM cards (known as "White SIM" or "خط سفید").

Every time a profile is scanned, a record is committed to this repository within seconds. This archive exists to provide verifiable, tamper-evident evidence that the data shown on the website is real and was genuinely retrieved from Twitter/X.

### What does "White SIM" mean?

A White SIM (خط سفید / سیمکارت سفید) is a special mobile line issued through Iran's state telecommunications infrastructure that is completely exempt from the national internet filtering system. Ordinary SIM cards in Iran route traffic through filtering gateways that block platforms such as X, Instagram, and YouTube. White SIM cards bypass those gateways entirely, giving the holder direct, unrestricted access to the global internet from inside Iran, with no VPN required.

These lines are not available to the public. They are estimated to be distributed to around 16,000 individuals out of Iran's 90 million population: senior government officials, commanders and members of the Islamic Revolutionary Guard Corps (IRGC), state television and radio journalists, editors of government-affiliated newspapers, judiciary figures, and intelligence personnel. Critics call them "blood SIM cards" (سیمکارت خونی) because many holders are involved in the violent suppression of protests.

Since X is blocked in Iran, an ordinary Iranian connecting through a VPN appears to be located in Germany, the Netherlands, or wherever their VPN server is. Someone using a White SIM connects directly from Iran, so X's "About this account" transparency feature shows "Iran" or "West Asia" as the connection country, which is the evidence this project collects and archives.

### What is in this repository?

**`profiles/<twitterId>/profile.json`**
A summary of the latest known state of the account, updated on every scan.

**`profiles/<twitterId>/snapshots/<snapshotId>.json`**
A full record of a single scan. Each file is written once and never modified. It contains:

- The structured fields extracted from the scan (username, bio, account location, connection source, etc.)
- The raw API response bodies returned directly by Twitter/X at the time of the scan

**`exports/profiles-<date>.csv`** and **`exports/snapshots-<date>.csv`**
Weekly full exports of all profiles and snapshots in CSV format.

### How does this prove the data is real?

Each snapshot file contains the raw JSON responses from Twitter's internal GraphQL API, specifically the `AboutAccountQuery` response. This response includes:

- `account_based_in`: the country from which the account most recently connected to X
- `source`: the connection source (e.g. "Iran Android App", "West Asia Android App")
- Internal fields such as GraphQL operation identifiers and response structures that are specific to Twitter's API at the time of the scan

These raw responses are Twitter's own output, not data we produce ourselves. Fabricating them convincingly would require reverse-engineering Twitter's internal API in precise detail, including versioned operation hashes and response schemas. The git history of this repository also provides an independent, append-only timestamp trail for every scan.

### What is stripped before publishing?

One field is removed from the raw payload before it is committed here: `relationship_perspectives`. This field reveals whether the scanning account follows or is followed by the scanned account. It contains no authentication credentials and its removal does not affect the proof of origin in any way.

### How often is this repository updated?

Snapshot files are committed in real time, within seconds of each scan. The weekly CSV exports are committed every weekend.

---

## فارسی

### این مخزن چیست؟

این مخزن یک آرشیو عمومی است که به صورت خودکار توسط [WhiteSimWatch](https://whitesimwatch.com) نگهداری می‌شود. این پروژه حساب‌های توییتر/ایکس را که از طریق خط سفید (سیمکارت سفید) فعالیت می‌کنند ردیابی می‌کند.

هر بار که یک پروفایل اسکن می‌شود، یک رکورد در عرض چند ثانیه به این مخزن اضافه می‌شود. هدف از این آرشیو ارائه شواهدی قابل تأیید و غیرقابل دستکاری است که نشان می‌دهد داده‌های نمایش داده شده در وبسایت واقعی هستند و به طور مستقیم از توییتر/ایکس دریافت شده‌اند.

### خط سفید چیست؟

خط سفید یا سیمکارت سفید، یک خط موبایل ویژه است که مستقیماً از طریق زیرساخت مخابراتی دولتی ایران صادر می‌شود و به طور کامل از سیستم فیلترینگ ملی معاف است. اینترنت سیمکارت‌های عادی از طریق درگاه‌های فیلترینگ عبور می‌کند که پلتفرم‌هایی مثل ایکس، اینستاگرام و یوتیوب را مسدود می‌کنند. اما سیمکارت‌های سفید این موانع را کاملاً دور می‌زنند و دسترسی مستقیم و بدون محدودیت به اینترنت جهانی را از داخل ایران فراهم می‌کنند، بدون نیاز به فیلترشکن.

این خطوط در دسترس عموم نیستند. تخمین زده می‌شود که از جمعیت ۹۰ میلیونی ایران، تنها حدود ۱۶ هزار نفر از آن‌ها استفاده می‌کنند: مقامات ارشد دولتی، فرماندهان و اعضای سپاه پاسداران، خبرنگاران صداوسیما، مدیران روزنامه‌های دولتی، مقامات قضایی و پرسنل اطلاعاتی. منتقدان از آن‌ها با عنوان «سیمکارت خونی» یاد می‌کنند، چرا که بسیاری از صاحبان این خطوط در سرکوب خشونت‌آمیز اعتراضات نقش داشته‌اند.

از آنجا که ایکس در ایران مسدود است، یک ایرانی معمولی که با فیلترشکن متصل می‌شود، در سرور فیلترشکن خود (مثلاً آلمان یا هلند) نشان داده می‌شود. اما صاحب سیمکارت سفید مستقیماً از ایران متصل می‌شود و به همین دلیل قابلیت «درباره این حساب» در ایکس، «ایران» یا «آسیای غربی» را به عنوان کشور اتصال نشان می‌دهد و همین، مدرکی است که این پروژه جمع‌آوری و آرشیو می‌کند.

### محتوای این مخزن چیست؟

**`profiles/<twitterId>/profile.json`**
خلاصه‌ای از آخرین وضعیت شناخته شده حساب که در هر اسکن به‌روزرسانی می‌شود.

**`profiles/<twitterId>/snapshots/<snapshotId>.json`**
رکورد کامل یک اسکن. هر فایل یک بار نوشته می‌شود و هرگز تغییر نمی‌کند. این فایل شامل موارد زیر است:

- فیلدهای ساختاریافته استخراج‌شده از اسکن (نام کاربری، بیو، موقعیت حساب، منبع اتصال و غیره)
- بدنه‌های خام پاسخ API که مستقیماً توسط توییتر/ایکس در زمان اسکن برگردانده شده‌اند

**`exports/profiles-<date>.csv`** و **`exports/snapshots-<date>.csv`**
صادرات کامل هفتگی از تمام پروفایل‌ها و اسنپ‌شات‌ها در قالب CSV.

### این چگونه ثابت می‌کند که داده‌ها واقعی هستند؟

هر فایل اسنپ‌شات شامل پاسخ‌های خام JSON از API داخلی GraphQL توییتر است، به ویژه پاسخ `AboutAccountQuery`. این پاسخ شامل موارد زیر است:

- `account_based_in`: کشوری که حساب اخیراً از آنجا به ایکس متصل شده است
- `source`: منبع اتصال (مثلاً "Iran Android App" یا "West Asia Android App")
- فیلدهای داخلی مانند شناسه‌های عملیات GraphQL و ساختارهای پاسخ که مختص API توییتر در زمان اسکن هستند

این پاسخ‌های خام، خروجی مستقیم توییتر هستند و ما آن‌ها را تولید نکرده‌ایم. جعل آن‌ها به صورت متقاعدکننده نیازمند مهندسی معکوس دقیق API داخلی توییتر است. تاریخچه git این مخزن نیز یک زنجیره زمانی مستقل و فقط افزایشی برای هر اسکن فراهم می‌کند.

### چه چیزی قبل از انتشار حذف می‌شود؟

یک فیلد از داده‌های خام قبل از ثبت در این مخزن حذف می‌شود: `relationship_perspectives`. این فیلد نشان می‌دهد که آیا حساب اسکنر با حساب اسکن‌شده رابطه دنبال‌کردن دارد یا نه. این فیلد هیچ اطلاعات احراز هویتی ندارد و حذف آن هیچ تأثیری بر اثبات منشأ داده‌ها ندارد.

### این مخزن چه زمانی به‌روزرسانی می‌شود؟

فایل‌های اسنپ‌شات در زمان واقعی، چند ثانیه پس از هر اسکن، ثبت می‌شوند. صادرات CSV هفتگی هر آخر هفته ثبت می‌شود.
