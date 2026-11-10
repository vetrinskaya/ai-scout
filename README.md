# ИИ-скаут

Раз в неделю приносит 3–5 находок, которые стоят времени фаундера и маркетинговой команды:

- **ИИ-инструменты:** креативы, аналитика, тестирование;
- **рекламные платформы:** Meta, Google, TikTok, Apple, AppsFlyer;
- **агенты и модели:** новые модели, MCP, кейсы автоматизации.

Каждую находку скаут сверяет с первоисточником: сайтом компании, changelog, репозиторием. Поисковые сводки регулярно пересказывают продукты, которых нет, поэтому в конце отчёта есть блок «Не прошло проверку».

Я пользуюсь таким скаутом сама. Это его версия для вас: без моего контекста, с местом под ваш.

[Аня Ветринская](https://vetrinskaya.com), growth co-founder

## Что нужно

[Claude](https://claude.ai/download) с задачами по расписанию: десктоп-приложение (Cowork или Claude Code) или Claude Code в терминале. Подписка Pro или выше.

## Как поставить (5 минут)

1. Скачайте [`SKILL.md`](SKILL.md).
2. Откройте его и заполните блок «КОНТЕКСТ»: продукт, рынки, каналы, команда, что сейчас важнее всего. Чем точнее, тем меньше шума в отчёте.
3. Откройте Claude, приложите файл и напишите:
   > Создай из этого файла задачу по расписанию: каждый понедельник в 9:00.
4. Попросите Claude запустить задачу один раз сразу, чтобы посмотреть первый отчёт.

Отчёт появится в истории запусков задачи.

## Отчёт в Telegram (по желанию)

1. Создайте бота у [@BotFather](https://t.me/BotFather) и скопируйте токен.
2. Напишите своему боту любое сообщение. Затем откройте `https://api.telegram.org/bot<ТОКЕН>/getUpdates` и найдите `"chat":{"id":...}`: это ваш chat id.
3. Добавьте обе переменные в `~/.claude/settings.json`:
   ```json
   {
     "env": {
       "TELEGRAM_BOT_TOKEN": "ваш токен",
       "TELEGRAM_CHAT_ID": "ваш chat id"
     }
   }
   ```
   Токен храните только там: не вставляйте его в `SKILL.md` и не выкладывайте в репозиторий.

## Как настроить под себя

- **Темы и источники** правятся в шагах 1–2 файла `SKILL.md`.
- **Ритм.** Можно запускать скаута каждый день, тогда в шаге 1 замените «7 дней» на «1–2 дня».
- **Язык.** Хотите отчёт на английском, допишите это в блок «КОНТЕКСТ».

## Хотите больше

Скаут: один из модулей [Marketing Shared Brain](https://vetrinskaya.com/#formats): общей памяти маркетинга для команды и ИИ-агентов. Если нужно встроить такие агенты в ваш маркетинг, [расскажите о проекте](https://vetrinskaya.com/brief).

---

## English

A weekly AI scout for founders and marketing teams: 3–5 verified picks on AI marketing tools, ad platforms (Meta, Google, TikTok, Apple, AppsFlyer), and agents and models. Every pick is checked against a primary source; what failed the check is listed separately. Download `SKILL.md`, fill in the CONTEXT block, and ask Claude to schedule it every Monday. The prompt is in Russian; add "write the report in English" to the context block to get English output.

License: MIT
