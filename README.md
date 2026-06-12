# Jikoku — landing page

Двуязычный (RU/EN) лендинг для проверки спроса: вейтлист по email + опрос интереса
к будущим фичам. Статика, готова под GitHub Pages.

## Структура
- `index.html` — вся страница (стили и скрипты внутри)
- `assets/screenshot.png` — реальный скриншот приложения
- `assets/icon.png` — иконка

## Сбор email (уже настроен)
Форма на сайте отправляет email в приватную Google-таблицу **«Jikoku — waitlist»**
через Google Apps Script (web app, доступ Anyone). Endpoint зашит в `index.html`
(`SHEET_ENDPOINT`). Боты отсекаются honeypot-полем `company`.
Колонки в таблице: Date · Email · Lang · Source. Экспорт в CSV — через таблицу.

## Статистика визитов (уже настроена)
Подключён GoatCounter — дашборд: **https://jikoku.goatcounter.com**
(приватный, без кук). Считает визиты и события: `cta-notify`, `want-email`, `want-slots`.

## Как опубликовать (сделать сайт живым)
1. Сделать репозиторий публичным:
   `gh repo edit glpkv/jikoku-landing --visibility public --accept-visibility-change-consequences`
2. Включить Pages с ветки `main`, папка `/ (root)`:
   `gh api -X POST repos/glpkv/jikoku-landing/pages -f source.branch=main -f source.path=/`
3. Сайт будет на **https://glpkv.github.io/jikoku-landing/** (1–2 мин на сборку).

## Какие сигналы считаются
- `cta-notify` — клик по главной кнопке вейтлиста
- `want-email` — голос «хочу почту (iCloud + Exchange) в приложении»
- `want-slots` — голос «хочу отправлять свободные слоты людям»
- собранные email — в Google-таблице «Jikoku — waitlist»

Визиты и события (cta-notify / want-email / want-slots) — в дашборде GoatCounter.
Email — в Google-таблице.
