<div align="center">
  <img src="Preview.jpg" alt="PGClock Lite Preview" width="900">
</div>

<h1 align="center">PGClock Lite</h1>

<p align="center">
  نسخهٔ سبک — قالب سریع صفحهٔ اشتراک برای Pasarguard
</p>

<p align="center">
  <a href="#نصب-خودکار">نصب خودکار</a> ·
  <a href="#نصب-دستی">نصب دستی</a> ·
  <a href="#تنظیمات-پنل">تنظیمات پنل</a> ·
  <a href="#نسخه‌های-دیگر">نسخه‌های دیگر</a>
</p>

---

## ویژگی‌ها

- رابط سبک و سریع برای موبایل، تبلت و دسکتاپ
- اطلاعات اشتراک
- اپلیکیشن‌ها و اعلان‌ها از پنل
- کپی، QR و دانلود WireGuard
- تشخیص OS و مرتب‌سازی اپ‌ها
- بهینه‌سازی برای دستگاه‌های ضعیف
- یک فایل HTML — بدون Node.js و build

---

## نصب خودکار

روی سرور **Ubuntu** با Pasarguard نصب‌شده:

```bash
curl -fsSL https://raw.githubusercontent.com/Mrclocks/PGClockLite/main/install.sh -o /tmp/pgclock-install.sh && sudo bash /tmp/pgclock-install.sh
```

یا:

```bash
wget -qO /tmp/pgclock-install.sh https://raw.githubusercontent.com/Mrclocks/PGClockLite/main/install.sh && sudo bash /tmp/pgclock-install.sh
```

در منو گزینه **۱) PGClock Lite** را انتخاب کنید.

### اسکریپت چه کار می‌کند؟

1. منوی انتخاب نسخه (`Lite` / `PGClock` / `Pro`)
2. ذخیرهٔ `index.html` در:

```text
/var/lib/pasarguard/templates/subscription/index.html
```

3. به‌روزرسانی `/opt/pasarguard/.env`:

```env
CUSTOM_TEMPLATES_DIRECTORY="/var/lib/pasarguard/templates/"
SUBSCRIPTION_PAGE_TEMPLATE="subscription/index.html"
```

4. اجرای `pasarguard restart`

> **پیش‌نیازها:** `wget`، `curl`، `python3`

---

## نصب دستی

### ۱. دانلود قالب

```bash
sudo mkdir -p /var/lib/pasarguard/templates/subscription/
sudo wget -N -O /var/lib/pasarguard/templates/subscription/index.html \
  https://raw.githubusercontent.com/Mrclocks/PGClockLite/main/index.html
```

### ۲. تنظیم Pasarguard

```bash
sudo nano /opt/pasarguard/.env
```

اضافه یا به‌روز کنید:

```env
CUSTOM_TEMPLATES_DIRECTORY="/var/lib/pasarguard/templates/"
SUBSCRIPTION_PAGE_TEMPLATE="subscription/index.html"
```

### ۳. راه‌اندازی مجدد

```bash
sudo pasarguard restart
```

---

## تنظیمات پنل

1. پنل Pasarguard → **Settings → Subscription**
2. ویرایش **announcement** و **announcement link**
3. افزودن/ویرایش اپ‌ها در بخش apps

---

## نسخه‌های دیگر

- [PGClock](https://github.com/Mrclocks/PGClock) — نسخهٔ استاندارد
- [PGClock Pro](https://github.com/Mrclocks/PGClockPRO) — برند، زیرعنوان و لوگوی سفارشی
