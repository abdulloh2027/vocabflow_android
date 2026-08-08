# VocabFlow — Android App (Capacitor wrapper)

Bu loyiha `https://vocab-flow-gilt.vercel.app/` saytini Android ilova
(APK/AAB) ko'rinishida o'raydi. Sayt yangilansa, ilovani qayta build
qilmasdan ham o'zgarishlar avtomatik ko'rinadi.

## 1-QADAM: GitHub'ga yuklash

Avvalgi `vocabflow_api` repo'sini qanday yuklagan bo'lsangiz, xuddi shunday
(CMD orqali `git init/add/commit/push` yoki GitHub'ning "Upload files"
tugmasi orqali) bu papkani ham **yangi, alohida** repo'ga yuklang (masalan:
`vocabflow-android`).

## 2-QADAM: APK avtomatik build bo'ladi

Fayllarni yuklaganingizdan so'ng, repo ichidagi **"Actions"** bo'limiga
o'ting. Workflow avtomatik ishga tushadi (3-5 daqiqa). Tugagach:

- Workflow natijasini oching → pastda **"Artifacts"** qismida
  **`VocabFlow-debug-apk`** faylini yuklab oling.
- Ichida `app-debug.apk` bor — telefonga o'rnatish uchun tayyor.

## 3-QADAM: Play Market uchun imzolangan (signed) versiya

Play Market'ga chiqarish uchun keystore (imzo kaliti) kerak — bu haqda
to'liq qadamlar avval sizga yuborilgan `vocabflow-android.zip`dagi
README'da bor edi:

1. `keytool -genkeypair -v -keystore vocabflow-release.keystore -alias vocabflow -keyalg RSA -keysize 2048 -validity 10000`
2. Keystore faylini base64'ga o'tkazib, GitHub repo Settings → Secrets →
   Actions bo'limiga quyidagi nomlar bilan qo'shing:
   `RELEASE_KEYSTORE_BASE64`, `RELEASE_KEYSTORE_PASSWORD`,
   `RELEASE_KEY_ALIAS`, `RELEASE_KEY_PASSWORD`.
3. Qayta push/"Re-run" qiling — endi `VocabFlow-release-aab` ham paydo
   bo'ladi, shuni Play Console'ga yuklaysiz.

## Muhim eslatmalar

- Ilova nomi/paket ID: `uz.linguistpro.vocabflow`.
- Ilova saytni WebView ichida ochadi — internet bo'lmasa ishlamaydi.
- Mikrofon (talaffuz mashqi) uchun ruxsat AndroidManifest'ga qo'shilgan.
