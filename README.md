<div dir="rtl">

# Saturation Boost

یک ماژول کوچک برای KernelSU / Magisk که اشباع رنگ (Saturation) نمایشگر را در هر بار بوت، با استفاده از SurfaceFlinger روی **۱.۱** تنظیم می‌کند.

![Version](https://img.shields.io/badge/version-1.1-blue)
![Root](https://img.shields.io/badge/KernelSU%20%7C%20Magisk-supported-green)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

[English README](README.md)

## ویژگی‌ها

- اعمال خودکار سچوریشن `1.1` بعد از هر بار بوت
- بدون تغییر در فایل‌های سیستم (systemless)
- سبک: فقط یک اسکریپت `service.sh`
- قابل شخصی‌سازی آسان

## پیش‌نیازها

- گوشی اندرویدی با روت از طریق [KernelSU](https://kernelsu.org/) یا [Magisk](https://github.com/topjohnwu/Magisk)
- رامی که از فراخوانی سچوریشن SurfaceFlinger (کد `1022`) پشتیبانی کند

## نصب

1. فایل `saturation_boost.zip` را از بخش [Releases](../../releases) دانلود کنید.
2. برنامه **KernelSU Manager** (یا Magisk) را باز کنید و به تب **Module** بروید.
3. دکمه نصب را بزنید و فایل zip را انتخاب کنید.
4. گوشی را ریبوت کنید.

## تنظیمات

برای تغییر مقدار سچوریشن، فایل `service.sh` را داخل پوشه ماژول ویرایش کنید:

```sh
service call SurfaceFlinger 1022 f 1.1
```

عدد `1.1` را با مقدار دلخواه جایگزین کنید (عدد `1.0` یعنی حالت پیش‌فرض و بدون تغییر).

مسیر ماژول روی گوشی:

```
/data/adb/modules/saturation_boost/service.sh
```

## برگرداندن بدون حذف ماژول

با دسترسی روت (ترموکس یا adb shell):

```sh
su
service call SurfaceFlinger 1022 f 1.0
```

یا ماژول را در منیجر غیرفعال کنید و ریبوت بزنید.

## حذف ماژول

از تب Module در KernelSU Manager / Magisk گزینه Uninstall را بزنید و ریبوت کنید.

حذف دستی:

```sh
su
touch /data/adb/modules/saturation_boost/remove
reboot
```

## ساختار ماژول

```
saturation_boost/
├── module.prop    # اطلاعات ماژول
└── service.sh     # اعمال سچوریشن بعد از اتمام بوت
```

## عیب‌یابی

- **بعد از ریبوت تغییری دیده نمی‌شود:** بعضی رام‌ها (مثلاً برخی نسخه‌های MIUI/HyperOS) ممکن است از کد `1022` پشتیبانی نکنند. زمان انتظار داخل `service.sh` را بیشتر کنید یا دستور را دستی در ترمینال روت تست کنید.
- **بوت‌لوپ:** از ریکاوری یا Safe Mode، فایلی با نام `disable` داخل پوشه ماژول بسازید:
  `/data/adb/modules/saturation_boost/disable`

## سلب مسئولیت

استفاده از این ماژول بر عهده خود شماست. سازنده مسئولیتی در قبال آسیب احتمالی به دستگاه ندارد.

## لایسنس

MIT

</div>
