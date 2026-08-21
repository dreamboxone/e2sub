# e2sub — Live Subtitle Translator

[فارسی](#فارسی) · [English](#english)

---

## فارسی

`e2sub` یک افزونهٔ Enigma2 با نام نمایشی **Live Subtitle Translator** است که
زیرنویس‌های متنی زندهٔ شبکه‌های تلویزیونی را با حفظ زمان‌بندی به فارسی ترجمه
می‌کند. نسخهٔ نخست برای Dreambox One UHD و بسته‌های Debian (`.deb`) طراحی شده
است.

### قابلیت‌ها

- ترجمهٔ زیرنویس متنی DVB/Teletext به فارسی
- ادامهٔ خودکار فعالیت پس از تعویض کانال
- بی‌اثر ماندن روی کانال‌هایی که زیرنویس متنی ندارند
- پردازش شبکه و Demux خارج از Thread اصلی Enigma2
- صف محدود و حذف ترجمه‌های دیررس برای جلوگیری از کندی پخش
- نمایش زیرنویس اصلی و پیام کوتاه هنگام قطع سرویس ترجمه
- انتخاب خودکار یا دستی Track زیرنویس
- تنظیم اندازه و رنگ فونت، پس‌زمینه، موقعیت، سایه و تأخیر
- فونت فارسی Vazirmatn
- لاگ موقت با سقف قطعی ۵۱۲ کیلوبایت
- حذف خودکار فایل نصب از `/tmp` و ری‌استارت Enigma2
- محافظت انتشار با مبهم‌سازی، SHA-256 و امضای RSA-3072

### دستگاه هدف

| مورد | مقدار |
|---|---|
| Version | `1.0.1` |
| Receiver | Dreambox One UHD |
| Image | DreamOS / OpenDreambox 2.6 |
| Architecture | arm64 / aarch64 |
| Python | 2.7.13 |
| Package | Debian `.deb` |
| Translation model | `gemini-3.5-flash-lite` |

کد تا حد ممکن با Python 3 نیز سازگار نگه داشته شده، اما هدف و آزمون اصلی
نسخهٔ فعلی DreamOS با Python 2.7.13 است. مسیر API Key برای Vu+ نیز در کد
پیش‌بینی شده، ولی Vu+ در این نسخه پشتیبانی و آزمون رسمی ندارد.

### محدودیت نسخهٔ نخست

نسخهٔ فعلی فقط Trackهای **متنی Teletext/DVB** را ترجمه می‌کند. زیرنویس‌های
تصویری DVB/Bitmap به OCR نیاز دارند و پشتیبانی نمی‌شوند. افزونه Track تصویری
را نادیده می‌گیرد و در پخش تلویزیون دخالت نمی‌کند.

### API Key

فایل باید فقط شامل خود API Key و بدون نام متغیر یا متن اضافی باشد:

- Dreambox: `/root/apikey.txt`
- Vu+، برای توسعهٔ آینده: `/home/root/apikey.txt`

```sh
chmod 600 /root/apikey.txt
```

API Key داخل بسته قرار نمی‌گیرد، در لاگ نوشته نمی‌شود و هنگام حذف افزونه نیز
پاک نخواهد شد.

### نصب

فایل انتشار را در `/tmp` قرار دهید و نصب کنید:

```sh
dpkg -i /tmp/enigma2-plugin-extensions-e2sub_1.0.1_arm64.deb
```

پس از پایان نصب، فایل نصب e2sub از `/tmp` حذف و Enigma2 با چند ثانیه تأخیر
به‌صورت خودکار ری‌استارت می‌شود.

### استفاده و تنظیمات

1. وارد فهرست Plugins شوید.
2. **Live Subtitle Translator** را باز کنید.
3. `Enable Live Subtitle Translator` را فعال کنید.
4. Track را روی `Automatic` بگذارید یا Track متنی را دستی انتخاب کنید.
5. تنظیمات را با کلید سبز ذخیره کنید.

تنظیمات موجود:

- Subtitle track
- Persian font size
- Subtitle text color
- Background opacity
- Vertical position
- Text shadow
- Translation delay، از `0.0` تا `5.0` ثانیه

نسخه و `youtube.com/@routekernel` در صفحهٔ تنظیمات نمایش داده می‌شوند. نام
ارائه‌دهندهٔ مدل ترجمه در رابط کاربری نمایش داده نمی‌شود.

### همگام‌سازی و کارایی

هر Cue با زمان دریافت و شناسهٔ نسل کانال ثبت می‌شود. پاسخ کانال قبلی یا پاسخ
رسیده پس از پایان مهلت Cue نمایش داده نمی‌شود. شبکه، ترجمه و خواندن Teletext
خارج از Thread اصلی Enigma2 انجام می‌شوند. صف ورودی عمداً کوچک است تا در
اینترنت کند، زیرنویس قدیمی انباشته نشود و پخش تلویزیون تحت تأثیر قرار نگیرد.

Teletext زمان پایان صریح ندارد؛ Header صفحهٔ بعدی Cue جاری را می‌بندد و یک
Timeout محافظ نیز متن باقی‌مانده را پاک می‌کند.

### فایل لاگ

```text
/tmp/e2sub.log
```

لاگ با ریبوت پاک می‌شود و هرگز از `524288` بایت بیشتر نمی‌شود. هنگام رسیدن به
سقف، قدیمی‌ترین اطلاعات حذف می‌شوند. لاگ نام و مدل رسیور، Image، معماری، وضعیت
اینترنت، وضعیت سرویس ترجمه و خطاهای عمومی را ثبت می‌کند؛ API Key و متن زیرنویس
ثبت نمی‌شوند.

### هزینه و حریم خصوصی

مدل مورد استفاده دارای Free Tier و پلن پولی است. سهمیه، قیمت و سیاست داده ممکن
است تغییر کند؛ صفحهٔ رسمی
[Gemini API Pricing](https://ai.google.dev/gemini-api/docs/pricing) را بررسی
کنید. در Free Tier ممکن است داده‌ها برای بهبود محصولات Google استفاده شوند.

### حذف و رفع اشکال

```sh
dpkg -r enigma2-plugin-extensions-e2sub
```

حذف افزونه به `/root/apikey.txt` یا `/home/root/apikey.txt` دست نمی‌زند.

- اگر ترجمه انجام نمی‌شود، وجود و مجوز `/root/apikey.txt` را بررسی کنید.
- نمایش زیرنویس اصلی یعنی شبکه/سرویس در دسترس نیست یا ترجمه دیر رسیده است.
- اگر روی یک کانال اتفاقی نمی‌افتد، احتمالاً Track متنی ندارد.
- برای تشخیص خطا، `/tmp/e2sub.log` را مشاهده کنید.

جزئیات معماری در [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) و روش ساخت و
امضا در [`docs/BUILD.md`](docs/BUILD.md) قرار دارد.

---

## English

`e2sub`, shown in Enigma2 as **Live Subtitle Translator**, translates live text
television subtitles into Persian while preserving cue timing. The first
release targets Dreambox One UHD and Debian (`.deb`) packages.

### Features

- Live Persian translation of text DVB/Teletext subtitles
- Automatic continuation after channel changes
- No processing on channels without a supported text track
- Network and demux work isolated from the Enigma2 UI/playback thread
- Bounded queues that discard late work instead of delaying television
- Automatic fallback to the original subtitle with a short error notice
- Automatic or manual subtitle-track selection
- Configurable font size, color, background, position, shadow, and delay
- Bundled Vazirmatn Persian font
- Volatile log with a strict 512 KiB maximum
- Automatic installer removal from `/tmp` and an Enigma2 restart
- Release hardening through obfuscation, SHA-256, and RSA-3072 signatures

### Target platform

| Item | Value |
|---|---|
| Version | `1.0.1` |
| Receiver | Dreambox One UHD |
| Image | DreamOS / OpenDreambox 2.6 |
| Architecture | arm64 / aarch64 |
| Python | 2.7.13 |
| Package | Debian `.deb` |
| Translation model | `gemini-3.5-flash-lite` |

The source remains Python 3 compatible where practical, but the primary target
and test environment is DreamOS with Python 2.7.13. A future Vu+ API-key path is
prepared in the platform layer; Vu+ is not officially supported or tested yet.

### Phase-one limitation

This release supports **text Teletext/DVB tracks only**. Bitmap DVB subtitles
require OCR and are not supported. Bitmap tracks are ignored without affecting
television playback.

### API key

The file must contain only the API key, with no variable name or extra text:

- Dreambox: `/root/apikey.txt`
- Future Vu+ support: `/home/root/apikey.txt`

```sh
chmod 600 /root/apikey.txt
```

The key is never packaged, logged, copied, or removed during uninstallation.

### Installation

Copy the release to `/tmp` and install it:

```sh
dpkg -i /tmp/enigma2-plugin-extensions-e2sub_1.0.1_arm64.deb
```

After installation, the e2sub installer is removed from `/tmp` and Enigma2 is
restarted automatically after a short delay.

### Usage and settings

1. Open the Enigma2 Plugins menu.
2. Open **Live Subtitle Translator**.
3. Enable `Enable Live Subtitle Translator`.
4. Keep `Subtitle track` on `Automatic`, or select a text track manually.
5. Press the green key to save.

Available settings:

- Subtitle track
- Persian font size
- Subtitle text color
- Background opacity
- Vertical position
- Text shadow
- Translation delay from `0.0` to `5.0` seconds

The settings screen includes the version and `youtube.com/@routekernel`. The
translation-provider name is intentionally absent from the user interface.

### Synchronization and performance

Every cue carries an arrival time and channel-generation token. Results from a
previous channel and results arriving after the cue deadline are discarded.
Teletext demuxing, network requests, and translation run outside the Enigma2
main thread. Small input queues prevent stale subtitles from accumulating or
affecting playback on slow connections.

Teletext has no explicit cue end time. A new page header closes the current cue,
with a defensive timeout clearing orphaned text.

### Log

```text
/tmp/e2sub.log
```

The log is cleared by a reboot and can never exceed `524288` bytes. Rotation
removes the oldest records. It includes receiver name/model, image,
architecture, internet status, translation-service status, and general errors.
It never includes the API key or subtitle content.

### Cost and privacy

The model offers Free Tier and paid usage. Quotas, pricing, and data-use policy
may change; consult the official
[Gemini API pricing page](https://ai.google.dev/gemini-api/docs/pricing). Free
Tier data may be used by Google to improve its products.

### Uninstallation and troubleshooting

```sh
dpkg -r enigma2-plugin-extensions-e2sub
```

Uninstallation does not remove `/root/apikey.txt` or
`/home/root/apikey.txt`.

- No translation: check `/root/apikey.txt` and its permissions.
- Original subtitles shown: the network/service is unavailable or the result
  arrived too late.
- Nothing happens on one channel: it probably has no text subtitle track.
- Diagnostics: inspect `/tmp/e2sub.log`.

See [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) for the technical design and
[`docs/BUILD.md`](docs/BUILD.md) for versioning, signing, and release builds.

### Credits

- Project/channel: [routekernel](https://youtube.com/@routekernel)
- Persian font: Vazirmatn, distributed under SIL Open Font License 1.1; the
  license is bundled with the plugin.
