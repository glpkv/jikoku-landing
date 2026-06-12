# Jikoku — landing page

Двуязычный (RU/EN) лендинг для проверки спроса: вейтлист по email + опрос интереса
к будущим фичам. Статика, готова под GitHub Pages.

## Структура
- `index.html` — вся страница (стили и скрипты внутри)
- `assets/screenshot.png` — реальный скриншот приложения
- `assets/icon.png` — иконка

## Перед запуском (2 правки в `index.html`)
1. **Счётчик визитов и кликов** — зарегистрируйся на https://www.goatcounter.com/signup,
   получишь код вида `xxx.goatcounter.com`. Замени `MYCODE` в теге `<script data-goatcounter=...>`.
2. **Сбор email** — создай форму на https://formspree.io, получишь ID.
   Замени `YOUR_FORM_ID` (1 место) на свой.

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
- собранные email — в дашборде Formspree

Всё видно в дашборде GoatCounter (визиты + события) и Formspree (email).
