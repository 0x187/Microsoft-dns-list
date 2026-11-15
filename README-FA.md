# DNS Blocklist مخصوص AdGuard Home - سرویس‌های Microsoft

تاریخ تهیه: 2026-11-15

این یک فهرست دسته‌بندی‌شده و غیرجامع از دامنه‌های مشاهده‌شده و مستندشده در سرویس‌های Windows 10/11 و Edge است؛ فهرست رسمی کامل یا فید دائماً به‌روزشونده نیست. نام دامنه و IPها ممکن است تغییر کنند. مسدودکردن DNS، جایگزین Group Policy یا Endpoint Management نیست.

## فایل‌ها
- `01-recommended.txt` : 28 قانون؛ News/MSN/Widgets/Spotlight/Telemetry. برای آزمون اولیه مناسب‌تر است. حتی همین فایل هم ممکن است اخبار، آب‌وهوا، صفحه New Tab و Diagnostics را مختل کند.
- `02-optional-services.txt` : 52 قانون؛ Bing و Edge config، Microsoft Store، OneDrive، Office، Teams، Xbox و Maps. فقط اگر تعطیلی این سرویس‌ها مطلوب است.
- `03-critical-not-recommended.txt` : 33 قانون؛ Windows Update، Edge Update، Defender/SmartScreen، فعال‌سازی، ورود، گواهی و اعلان‌ها. **برای کلاینت یا سرور عادی مناسب نیست!**
- `00-ALL-AGGRESSIVE-UNSAFE.txt` : 113 قانون در مجموع. همه سطوح؛ ریسک زیاد و به‌صورت پیش‌فرض توصیه نمی‌شود.
- `04-recommended-campus-clients-only.txt`: قوانین 01 با محدودکننده `$client=10.10.10.0/23` برای شبکه داخلی 10.10.10.0/23. اگر AdGuard فقط IP روتر/فورواردکننده را ببیند کار نمی‌کند؛ با Query Log آزمایش شود.

## نصب آسان در AdGuard Home
1. فایل دلخواه را باز کن و تمام محتوای آن را کپی کن.
2. برو `Filters -> Custom filtering rules`، قوانین را Paste و Save کن.
3. برای نگهداری به‌عنوان یک DNS blocklist مستقل، فایل TXT را در یک URL قابل‌دسترس (مانند raw.githubusercontent.com یا وب‌سرور داخلی) منتشر کن و از `Filters -> DNS blocklists -> Add blocklist -> Add a custom list` URL را ثبت کن.
4. از `Query Log` وضعیت Blocked را بررسی کن و سرویس‌های مهم، DNS نشت‌کردن و رفتار Edge/Update/Defender را چک کن.

## نحو
- `||example.com^` دامنه اصلی و تمام زیر‌دامنه‌ها را مسدود می‌کند.
- `@@||example.com^` استثنا یا allow برای همان دامنه می‌سازد؛ با توجه به اولویت قوانین موجود ممکن است احتیاج به بررسی داشته باشد.
- خطوط شروع‌شده با `!` کامنت هستند.
- صرفاً اضافه‌شدن فایل در رایانه، به معنی واردشدن خودکار لیست به AdGuard Home نیست.

## هشدار امنیتی
- استفاده از لیست 03 یا 00 روی ماشین‌های سازمانی که باید آپدیت/Defender/Sign-in فعال باشند توصیه نمی‌شود.
- در سطوح 01 و 02 ممکن است سرویس‌های دیگری که از endpoint مشترک استفاده می‌کنند اختلال پیدا کنند.
- هرگز دامنه‌های کلی `microsoft.com`، `live.com`، `azureedge.net`، `blob.core.windows.net` یا `bing.com` را کورکورانه مسدود نکن.
- DNS می‌تواند host را مسدود کند، نه path را؛ فیچرهای متفاوت Edge ممکن است یک host مشترک داشته باشند.
- شبکه‌هایی که DoH مستقیم به خارج دارند، ممکن است DNS سرور AdGuard Home را دور بزنند.

## منابع رسمی
- https://learn.microsoft.com/en-us/windows/privacy/manage-windows-11-endpoints
- https://learn.microsoft.com/en-us/windows/privacy/windows-11-endpoints-non-enterprise-editions
- https://learn.microsoft.com/en-us/deployedge/microsoft-edge-security-endpoints
- https://github.com/AdguardTeam/AdGuardHome/wiki/Hosts-Blocklists
- https://github.com/AdguardTeam/AdGuardHome/wiki/Clients
