# کیت PWA «حساب‌وکتاب مشترک»

این پوشه همه چیزهایی است که برای نصب‌شدن شدن اپ روی گوشی (و ساخت APK) لازم داری:

| فایل | توضیح |
|---|---|
| `index.html` | کد اصلی شما + متادیتای PWA در head + ثبت Service Worker (بقیه کد دست‌نخورده است) |
| `manifest.json` | شناسنامه کامل اپ (نام، رنگ، آیکون، اسکرین‌شات، حالت تمام‌صفحه) |
| `sw.js` | سرویس‌ورکر — فقط فایل‌های خود سایت را کش می‌کند؛ درخواست‌های API (گوگل‌شیت) دست‌نخورده عبور می‌کنند |
| `icon-192.png` و `icon-512.png` | آیکون اپ برای صفحه اصلی گوشی و فروشگاه‌ها |
| `icon-maskable-512.png` | آیکون مخصوص ماسک گرد اندروید |
| `screenshot-narrow.png` و `screenshot-wide.png` | اسکرین‌شات برای PWABuilder و نصب غنی در اندروید |

این نسخه همه هشدارهای PWABuilder (Service Worker، description، background_color، theme_color، screenshots) را رفع می‌کند.

آدرس سرور (`SERVER_URL`) داخل `index.html` همان قبلی است و نیازی به تغییر ندارد.

---

## گام ۱ — انتشار روی اینترنت (HTTPS اجباری است)

**راه ساده: GitHub Pages**
1. در github.com یک ریپوی **Public** بساز (مثلاً `hesab-ketab`).
2. «Add file → Upload files» → هر ۵ فایل این پوشه را بگذار و Commit کن.
3. `Settings → Pages → Branch: main → Save`
4. حدود یک دقیقه بعد آدرس `https://USERNAME.github.io/hesab-ketab/` فعال می‌شود.

**راه جایگزین (بدون گیت):** در netlify.com/drop پوشه را بکش و رها کن.

## گام ۲ — نصب روی گوشی (بدون APK، سریع‌ترین راه)

کروم گوشی → باز کردن آدرس صفحه → منوی ⋮ → **Add to Home screen**
اپ با آیکون اختصاصی و تمام‌صفحه باز می‌شود. برای هر دو نفر همین یک قدم کافی است.

## گام ۳ — ساخت APK واقعی با PWABuilder (بدون نصب هیچ ابزاری)

1. برو به `pwabuilder.com` و آدرس صفحه را وارد کن → **Start**
2. **Package for stores → Android**
3. Package ID مثلاً: `ir.mehdi.hesabketab` → **Download**
4. در zip دانلودی، فایل `app-release-signed.apk` آماده نصب است؛ همان را برای دوستت بفرست (تلگرام/واتساپ).

## راه جایگزین — Android Studio (WebView)

اگر کنترل کامل می‌خواهی: پروژه «Empty Views Activity» بساز، پرمیشن `INTERNET` را به Manifest اضافه کن و در `MainActivity` یک WebView با `javaScriptEnabled = true` و `domStorageEnabled = true` آدرس صفحه را باز کن (کد کامل در پیام چت آمده).

---

## یادآوری‌های مهم

- Web App را با دسترسی **Anyone** منتشر کن وگرنه لاگین کار نمیکند.
- `SETUP_KEY` در `Code.gs` را قبل از انتشار عوض کن.
- برای به‌روزرسانی `Code.gs` از همان Deployment قبلی استفاده کن (Manage deployments → Edit → Version: New version) تا آدرس `/exec` عوض نشود.
- بعد از تغییر `index.html` روی هاست، هر دو نفر نسخه جدید را بدون نصب مجدد می‌گیرند.
