# Mücevher Blok - Uygulamaya Çevirme Rehberi

Klasör yapısı:
- `www/` oyunun kendisi (index.html, simgeler, manifest, service worker)
- `capacitor.config.json` ve `package.json` Android/iOS paketi için hazır ayarlar

## Yol 1: Android uygulaması (APK/AAB) - Capacitor
Gerekenler: Node.js 18+ ve Android Studio.

1. Bu klasörde terminal aç: `npm install`
2. `npx cap add android`
3. `npx cap sync android`
4. `npx cap open android` (Android Studio açılır)
5. Android Studio'da Build > Build Bundle(s) / APK(s) ile APK veya Play Store için AAB üret.

Dikey ekrana kilitlemek için `android/app/src/main/AndroidManifest.xml` içindeki `<activity>` etiketine
`android:screenOrientation="portrait"` ekle.
Uygulama simgesi için `www/icons/icon-1024.png` dosyasını Android Studio > Image Asset aracında kullan.

## Yol 2: iOS (Mac ve Xcode gerekir)
`npx cap add ios`, `npx cap sync ios`, `npx cap open ios`

## Yol 3: Kodsuz, hızlı yöntem
1. `www/` klasörünü bir HTTPS adrese yükle (Netlify, GitHub Pages vb.).
2. https://www.pwabuilder.com adresine o adresi gir, Android paketini indir.

## Telefonda doğrudan deneme
`www/` klasörünü bir web sunucusuna koyup telefon tarayıcısında aç, "Ana ekrana ekle" ile uygulama gibi kullan.

## Notlar
- Oyun tamamen çevrimdışı çalışır. Yalnızca Google Fonts (Lilita One, Nunito) internet gerektirir. Yoksa sistem yazı tipine geçer. Tam çevrimdışı yazı tipi için font dosyalarını `www/` içine koyup `@font-face` ile bağla.
- Rekor ve kayıtlar `localStorage` ile saklanır, uygulama içinde de çalışır.
- Mağaza yayını için `capacitor.config.json` içindeki `appId` değerini kendi paket adınla değiştir.
