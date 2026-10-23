# IRON PLAN — Football Performance

## Установка на GitHub Pages
Загрузи `index.html`, `manifest.json`, `icon.svg` и `README.md` в корень репозитория. В GitHub: Settings → Pages → Deploy from a branch → `main` → `/(root)` → Save. После завершения сборки открой адрес Pages.

## Что есть
- Большая анкета футболиста и шаблоны тренировок.
- Дополнительные блоки для вратаря, центрального защитника, крайнего защитника, опорника, центрального и атакующего полузащитника, вингера и нападающего.
- Исключение становой тяги, румынской тяги и приседаний из шаблона.
- Отметки выполненных упражнений.
- Дневник тренировок с упражнениями, весами, подходами, повторами, RPE и заметками; экспорт CSV.
- Ориентировочный калькулятор КБЖУ; экспорт/импорт резервной копии JSON.
- Локальный профиль с ником и паролем (пароль хранится как PBKDF2-хэш).

## Важно про аккаунты
Локальная регистрация работает только в одном браузере/устройстве и не является настоящей серверной системой аккаунтов. Данные хранятся в localStorage Safari. Очистка данных сайта может их удалить. Не используй пароль от Google или других сайтов.
Кнопка Google пока объясняет, как подключить Firebase. Чтобы реализовать реальный Google sign-in и синхронизацию между устройствами, нужен Firebase Authentication + Firestore и настройка домена. Это нельзя безопасно включить только с помощью HTML без конфигурации проекта.

## Безопасность и спорт
КБЖУ — приблизительная оценка. Для спортсменов младше 18 лет не использовать агрессивный дефицит калорий; обсуди изменение веса с врачом/спортивным диетологом. Программа шаблонная, позиционные блоки дополняют командную работу. При боли, травме или медицинских ограничениях согласуй нагрузку со специалистом. Силовая и взрывная работа несовершеннолетних — под контролем квалифицированного тренера.


## Firebase setup status (important)

This archive is the current IRON PLAN web app plus Firebase setup templates. The app's existing profile and workout data still use this browser's local storage; simply creating a Firebase project or publishing Firestore rules does **not** connect the app to cloud sync. To enable real Google/email login and cross-device cloud saving, Firebase Auth and Firestore calls must be added to the app code and configured with your web app config. `firebase-config.example.js` is a template only, not a working config. Do not deploy it unchanged and do not share passwords or private service-account keys.

### Firebase console steps already completed
- Email/Password provider enabled.
- Google provider enabled.
- Firestore database created.
- Rules shown in the screenshots allow each signed-in user to access only `/users/{their UID}/...`.

### Next steps
1. Firebase Console → Project settings → Your apps → select the registered Web app.
2. Copy the **Firebase configuration object** (not a service-account key) into `firebase-config.example.js`, then rename it to `firebase-config.js`.
3. Keep Firestore rules user-scoped as in `firestore.rules.example.txt` and publish them.
4. The app still needs Firebase SDK integration in `index.html` before Google login/cloud sync will work. This ZIP does not claim that cloud integration is already active.
