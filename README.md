# e2sub — Live Subtitle Translator

[فارسی](#فارسی) · [English](#english)

---

<div dir="rtl" align="right">

<h2 id="فارسی">فارسی</h2>

<p>
<strong>Live Subtitle Translator</strong> افزونه‌ای برای Enigma2 است که
زیرنویس‌های متنی زندهٔ کانال‌های تلویزیونی را به فارسی ترجمه می‌کند.
</p>

<p><strong>نسخه ۱.۰.۱ برای این مشخصات آماده شده است:</strong></p>

<ul>
  <li>Dreambox One UHD</li>
  <li>DreamOS / OpenDreambox 2.6</li>
  <li>معماری arm64</li>
  <li>Python 2.7.13</li>
</ul>

<h3>قابلیت‌ها</h3>

<ul>
  <li>ترجمهٔ زیرنویس متنی DVB/Teletext به فارسی</li>
  <li>ادامهٔ خودکار پس از تعویض کانال</li>
  <li>نمایش زیرنویس اصلی هنگام قطع سرویس ترجمه</li>
  <li>تنظیم رنگ، اندازه، موقعیت، پس‌زمینه، سایه و تأخیر زیرنویس</li>
  <li>پردازش غیرهمزمان بدون مسدودکردن پخش تلویزیون</li>
  <li>لاگ موقت با سقف قطعی ۵۱۲ کیلوبایت</li>
</ul>

<h3>API Key</h3>

<p>فایل باید فقط شامل خود API Key باشد:</p>

<ul>
  <li>Dreambox: <code>/root/apikey.txt</code></li>
  <li>Vu+، برای توسعهٔ آینده: <code>/home/root/apikey.txt</code></li>
</ul>

<p>این فایل داخل بسته قرار نمی‌گیرد و با حذف افزونه نیز پاک نمی‌شود.</p>

<h3>نصب</h3>

<pre dir="ltr"><code>dpkg -i /tmp/enigma2-plugin-extensions-e2sub_1.0.1_arm64.deb</code></pre>

<p>
پس از نصب، فایل e2sub از پوشهٔ <code>/tmp</code> حذف و Enigma2 به‌صورت خودکار
ری‌استارت می‌شود.
</p>

<h3>استفاده</h3>

<ol>
  <li>از منوی Plugins وارد <strong>Live Subtitle Translator</strong> شوید.</li>
  <li>افزونه را فعال کنید.</li>
  <li>Track را روی Automatic بگذارید یا یک Track متنی انتخاب کنید.</li>
  <li>با کلید سبز تنظیمات را ذخیره کنید.</li>
</ol>

<blockquote>
نسخهٔ فعلی فقط زیرنویس متنی Teletext/DVB را پشتیبانی می‌کند؛ زیرنویس تصویری
DVB/Bitmap هنوز پشتیبانی نمی‌شود.
</blockquote>

<p>
لاگ افزونه در <code>/tmp/e2sub.log</code> قرار دارد. جزئیات بیشتر در
<a href="docs/ARCHITECTURE.md">معماری</a> و
<a href="docs/BUILD.md">راهنمای بیلد</a> نوشته شده است.
</p>

</div>

---

## English

**Live Subtitle Translator** is an Enigma2 plugin that translates live text
television subtitles into Persian.

Version `1.0.1` targets Dreambox One UHD, DreamOS/OpenDreambox 2.6, arm64, and
Python 2.7.13.

### Features

- Persian translation of text DVB/Teletext subtitles
- Automatic continuation after channel changes
- Original-subtitle fallback when translation is unavailable
- Configurable font, color, background, position, shadow, and delay
- Asynchronous processing that does not block television playback
- Volatile log with a strict 512 KiB limit

### API key

The file must contain only the API key:

- Dreambox: `/root/apikey.txt`
- Future Vu+ support: `/home/root/apikey.txt`

The key is never packaged or removed during uninstallation.

### Installation

```sh
dpkg -i /tmp/enigma2-plugin-extensions-e2sub_1.0.1_arm64.deb
```

The installer is removed from `/tmp`, and Enigma2 restarts automatically.

### Usage

1. Open **Live Subtitle Translator** from the Plugins menu.
2. Enable the plugin.
3. Keep track selection on `Automatic`, or select a text track.
4. Press the green key to save.

> This release supports text Teletext/DVB subtitles only. Bitmap DVB subtitles
> are not supported yet.

The log is available at `/tmp/e2sub.log`. See the
[architecture](docs/ARCHITECTURE.md) and [build guide](docs/BUILD.md) for
technical details.

Project/channel: [routekernel](https://youtube.com/@routekernel)

---

<div dir="rtl">

## 💚 حمایت از این پروژه

اگر این پروژه به کارتان آمده، می‌توانید با واریز تتر از آن حمایت کنید:

**USDT (تتر) — فقط شبکه BEP20 (BSC)**

</div>

```
0x56daaa6b76d88ee0c8dba8042121f4b77de0a813
```

<div dir="rtl">

> ⚠️ این آدرس فقط برای واریز تتر در شبکه BEP20 (BSC) است. واریز ارز دیگر یا از شبکه دیگر به این آدرس از دست می‌رود.

</div>

---

## 💚 Support this project

If this project has been useful to you, you can support it with Tether:

**USDT — BEP20 (BSC) network only**

```
0x56daaa6b76d88ee0c8dba8042121f4b77de0a813
```

> [!WARNING]
> This address is for USDT on the BEP20 (BSC) network only. Any other coin, or USDT sent over any other network, is lost.
