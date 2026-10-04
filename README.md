# NEON DROP — приложение для Android

## APK для установки на телефон (без компьютера)
1. Создай на GitHub новый репозиторий (например, neondrop-app).
2. Загрузи в корень (Add file → Upload files): index.html, package.json, capacitor.config.json, README.md, icon-only.png, icon-foreground.png, icon-background.png, splash.png.
3. Add file → Create new file → имя `.github/workflows/android.yml` → вставь содержимое android.yml → Commit.
4. Вкладка Actions → Build Android APK → Run workflow.
5. Через 5-10 минут открой завершённый запуск → внизу Artifacts → neondrop-apk. Внутри zip лежит app-debug.apk.
6. Поставь APK на Android (разреши установку из неизвестных источников).

Иконка и экран загрузки создаются автоматически из загруженных PNG. Если иконка осталась стандартной, открой лог шага "Generate icons and splash".

## Подписанный AAB для Google Play (по желанию)
1. На компьютере с Java создай ключ: `keytool -genkeypair -v -keystore release.keystore -alias neondrop -keyalg RSA -keysize 2048 -validity 10000`
2. Преврати файл в base64 (Mac/Linux: `base64 release.keystore`).
3. В репозитории: Settings → Secrets and variables → Actions → New secret. Создай KEYSTORE_BASE64, KEYSTORE_PASSWORD, KEY_ALIAS (neondrop), KEY_PASSWORD.
4. Создай файл `.github/workflows/android-release.yml` (содержимое из android-release.yml) и запусти его в Actions.
5. Скачай neondrop-aab и загрузи в Google Play Console. Ключ храни в надёжном месте, потерять его нельзя.

## iOS (IPA)
Нужны Mac с Xcode и платный аккаунт Apple Developer. Команды на Mac: npm install, npm run prepare-web, npx cap add ios, npx cap sync ios, npx cap open ios. Затем в Xcode: Team → Product → Archive → Distribute App.
