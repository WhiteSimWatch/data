# WhiteSimWatch / Data

**Transparency Archive: Public Scan Record**

[English](#english) | [فارسی](#فارسی)

---

## English

### What is this repository?

This repository is a public archive maintained automatically by [WhiteSimWatch](https://whitesimwatch.com). The project tracks Twitter/X accounts whose holders connect directly from Iran using unfiltered SIM cards issued by the state, known as "White SIM" or "خط سفید".

Every time a profile is scanned a record is committed to this repository within seconds. This archive exists so anyone can verify that the data shown on the website is real and was genuinely retrieved from Twitter/X.

### What does "White SIM" mean?

A White SIM or سیمکارت سفید is a special mobile line issued through Iran's state telecommunications infrastructure. It is completely exempt from the national internet filtering system. Ordinary SIM cards in Iran route traffic through filtering gateways that block platforms like X, Instagram and YouTube. White SIM cards bypass those gateways entirely and give the holder direct unrestricted access to the global internet from inside Iran with no VPN required.

These lines are not available to the public. An estimated 16,000 individuals out of Iran's 90 million population have them. They include senior government officials, IRGC commanders and members, state media journalists, editors at newspapers affiliated with the government, judiciary figures and intelligence personnel.

Since X is blocked in Iran an ordinary Iranian connecting through a VPN appears to be located wherever their VPN server is. That could be Germany or the Netherlands for example. Someone using a White SIM connects directly from Iran so the "About this account" section on X shows "Iran" or "West Asia" as the connection country. That is the evidence this project collects and archives.

### What is in this repository?

**`profiles/<twitterId>/profile.json`**
A summary of the latest known state of the account. Updated on every scan.

**`profiles/<twitterId>/snapshots/<snapshotId>.json`**
A full record of a single scan. Each file is written once and never modified. It contains the following.

- The structured fields extracted from the scan such as username, bio, account location and connection source
- The raw API response bodies returned directly by Twitter/X at the time of the scan

**`exports/profiles-<date>.csv`** and **`exports/snapshots-<date>.csv`**
Weekly full exports of all profiles and snapshots in CSV format.

### How does this prove the data is real?

Each snapshot file contains the raw JSON responses from Twitter's internal GraphQL API. The most important one is the `AboutAccountQuery` response which includes the following.

- `account_based_in` is the country from which the account most recently connected to X
- `source` is the connection source for example "Iran Android App" or "West Asia Android App"
- Internal fields such as GraphQL operation identifiers and response structures specific to Twitter's API at the time of the scan

These raw responses are Twitter's own output and not data we produce ourselves. Fabricating them convincingly would require reverse engineering Twitter's internal API in precise detail including versioned operation hashes and response schemas. The git history of this repository also provides an independent timestamp trail where records can only be appended and never altered.

### What is stripped before publishing?

One field called `relationship_perspectives` is removed from the raw payload before it is committed here. This field reveals whether the scanning account follows or is followed by the scanned account. It contains no authentication credentials and removing it does not affect the proof of origin in any way.

### How often is this repository updated?

Snapshot files are committed in real time within seconds of each scan. The weekly CSV exports are committed every weekend.

---

## فارسی

### این مخزن چیست؟

این مخزن یک آرشیو عمومی است که به صورت خودکار توسط [WhiteSimWatch](https://whitesimwatch.com) نگهداری می‌شود. این پروژه حساب‌های توییتر/ایکس را ردیابی می‌کند که صاحبانشان از طریق خط سفید و بدون نیاز به فیلترشکن مستقیما از ایران به این پلتفرم وصل می‌شوند.

هر بار که پروفایلی اسکن می‌شود رکورد آن ظرف چند ثانیه در این مخزن ثبت می‌شود. هدف این آرشیو این است که هر کسی بتواند تایید کند داده‌هایی که در وبسایت نمایش داده می‌شوند واقعی هستند و مستقیما از توییتر/ایکس گرفته شده‌اند.

### خط سفید چیست؟

خط سفید یا سیمکارت سفید یک خط موبایل ویژه است که از طریق زیرساخت مخابراتی دولتی ایران صادر می‌شود و به طور کامل از سیستم فیلترینگ ملی معاف است. سیمکارت‌های عادی در ایران ترافیک اینترنت را از درگاه‌های فیلترینگ رد می‌کنند که پلتفرم‌هایی مثل ایکس و اینستاگرام و یوتیوب را مسدود می‌کنند. اما سیمکارت‌های سفید این درگاه‌ها را کاملا دور می‌زنند و به صاحبشان دسترسی مستقیم و بدون محدودیت به اینترنت جهانی را از داخل ایران می‌دهند بدون نیاز به هیچ فیلترشکنی.

این خطوط در دسترس مردم عادی نیست. از جمعیت ۹۰ میلیونی ایران تخمین زده می‌شود فقط حدود ۱۶ هزار نفر این خطوط را در اختیار دارند. مقامات ارشد دولتی و فرماندهان و اعضای سپاه پاسداران و خبرنگاران صداوسیما و سردبیران روزنامه‌های وابسته به حکومت و مقامات قضایی و نیروهای اطلاعاتی.

از آنجا که ایکس در ایران فیلتر است یک ایرانی عادی که با فیلترشکن وصل می‌شود از دید ایکس در کشور سرور فیلترشکنش قرار دارد مثلا آلمان یا هلند. اما کسی که سیمکارت سفید دارد مستقیما از ایران وصل می‌شود و به همین دلیل بخش «درباره این حساب» در ایکس کشور اتصال را «ایران» یا «آسیای غربی» نشان می‌دهد. این همان مدرکی است که این پروژه جمع‌آوری و آرشیو می‌کند.

### محتوای این مخزن چیست؟

**`profiles/<twitterId>/profile.json`**
خلاصه‌ای از آخرین وضعیت شناخته‌شده حساب که با هر اسکن به‌روز می‌شود.

**`profiles/<twitterId>/snapshots/<snapshotId>.json`**
رکورد کامل یک اسکن. هر فایل فقط یک بار نوشته می‌شود و دیگر تغییر نمی‌کند. شامل موارد زیر است.

- فیلدهای ساختاریافته استخراج‌شده از اسکن مثل نام کاربری و بیو و موقعیت حساب و منبع اتصال
- پاسخ‌های خام API که مستقیما توسط توییتر/ایکس در لحظه اسکن برگردانده شده‌اند

**`exports/profiles-<date>.csv`** و **`exports/snapshots-<date>.csv`**
خروجی کامل هفتگی از تمام پروفایل‌ها و اسنپ‌شات‌ها در قالب CSV.

### این چطور ثابت می‌کند که داده‌ها واقعی هستند؟

هر فایل اسنپ‌شات حاوی پاسخ‌های خام JSON از API داخلی GraphQL توییتر است مشخصا پاسخ `AboutAccountQuery`. این پاسخ شامل موارد زیر است.

- `account_based_in` یعنی کشوری که حساب آخرین بار از آنجا به ایکس وصل شده
- `source` یعنی منبع اتصال مثلا "Iran Android App" یا "West Asia Android App"
- فیلدهای داخلی مثل شناسه‌های عملیات GraphQL و ساختار پاسخ‌ها که مختص API توییتر در زمان اسکن هستند

این پاسخ‌های خام خروجی خود توییتر هستند و ما آنها را تولید نکرده‌ایم. جعل قانع‌کننده این داده‌ها نیاز به مهندسی معکوس دقیق API داخلی توییتر دارد از جمله هش‌های عملیاتی نسخه‌بندی‌شده و اسکیمای پاسخ‌ها. تاریخچه گیت این مخزن هم یک زنجیره زمانی مستقل برای هر اسکن فراهم می‌کند که فقط امکان افزودن رکورد جدید دارد و رکوردهای قبلی قابل تغییر نیستند.

### چه چیزی قبل از انتشار حذف می‌شود؟

یک فیلد به نام `relationship_perspectives` از داده‌های خام قبل از ثبت در این مخزن حذف می‌شود. این فیلد نشان می‌دهد که آیا حساب اسکنر حساب مورد نظر را دنبال می‌کند یا نه. این فیلد هیچ اطلاعات احراز هویتی ندارد و حذفش تاثیری بر اثبات اصالت داده‌ها ندارد.

### این مخزن هر چند وقت به‌روز می‌شود؟

فایل‌های اسنپ‌شات در لحظه و ظرف چند ثانیه پس از هر اسکن ثبت می‌شوند. خروجی CSV هفتگی هم هر آخر هفته ثبت می‌شود.
