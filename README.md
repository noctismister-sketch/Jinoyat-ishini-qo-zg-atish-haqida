# Jinoyat Ishi — Android ilova (Capacitor)

Bu loyiha sizning HTML sahifangizni (`www/index.html`) Android APK ilovaga aylantiradi.
Hech qanday Android Studio kerak emas — hammasi GitHub Actions serverida avtomatik yig'iladi.

## 1-qadam — GitHub'ga yuklash

Terminalda (yoki GitHub Desktop'da) shu papka ichida:

```bash
git init
git add .
git commit -m "Jinoyat ishi ilovasi - boshlang'ich versiya"
git branch -M main
git remote add origin https://github.com/FOYDALANUVCHI_NOMI/REPO_NOMI.git
git push -u origin main
```

(`FOYDALANUVCHI_NOMI` va `REPO_NOMI` o'rniga o'zingizning GitHub username va repo nomingizni yozing. Repo'ni oldindan GitHub saytida "New repository" tugmasi orqali yarating — bo'sh, README'siz.)

## 2-qadam — APK avtomatik yig'iladi

Push qilgach, GitHub avtomatik ishga tushadi:

1. Repo sahifangizda **Actions** bo'limiga o'ting
2. "Build APK" ishi (workflow) ishlab turganini ko'rasiz (2-5 daqiqa davom etadi)
3. Ish tugagach, o'sha sahifaning pastida **Artifacts** bo'limidan
   `jinoyat-ishi-debug-apk` faylini yuklab oling — bu ZIP ichida `app-debug.apk` bor

## 3-qadam — Telefonga o'rnatish

APK faylni telefoningizga yuboring (Telegram, USB, Google Drive orqali — farqi yo'q) va oching.
Birinchi marta "Noma'lum manbalardan o'rnatish" (Install from unknown sources) ruxsatini so'rashi mumkin — buni yoqing.

---

## Ilova nomi va ID'ni o'zgartirish

`capacitor.config.json` faylida:
- `"appName"` — ilova nomi (telefon ekranida ko'rinadi)
- `"appId"` — noyob identifikator (masalan `uz.huquq.jinoyatishi`), Play Store'ga chiqarsangiz o'zgartirib bo'lmaydi, shuning uchun oldindan mos nom tanlang

## Ilova ikonkasini qo'shish (ixtiyoriy)

Standart Capacitor ikonkasi ishlatiladi. O'z logotipingizni qo'yish uchun:
1. 1024x1024 px PNG rasm tayyorlang
2. https://icon.kitchen yoki https://www.appicon.co saytida barcha o'lchamlarga generatsiya qiling
3. Natijadagi papkalarni `android/app/src/main/res/` ichiga joylashtiring (workflow har safar `android/` papkasini qaytadan yaratgani uchun, buni **workflow faylidagi** alohida qadam sifatida qo'shish kerak bo'ladi — kerak bo'lsa ayting, shu qismni ham qo'shib beraman)

## Play Store uchun signed (imzolangan) APK/AAB

Hozirgi workflow faqat **debug APK** yasaydi — bu sinov va shaxsiy foydalanish uchun yetarli.
Agar Google Play Store'ga chiqarish kerak bo'lsa, signing key yaratish va workflow'ga
GitHub Secrets orqali qo'shish kerak bo'ladi. Bu bosqichga yetganingizda ayting — signed
release build uchun workflow'ni kengaytirib beraman.

## Ilova mazmunini yangilash

Sahifa matnini/savollarni o'zgartirish uchun shunchaki `www/index.html` faylini tahrirlab,
qayta `git push` qiling — Actions avtomatik yangi APK yig'ib beradi.
