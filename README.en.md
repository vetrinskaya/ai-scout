# AI scout for marketing and advertising

[Русская версия](README.md)

An agent that finds new AI and advertising releases once a week and brings 3–5 picks that are worth the time of a founder and a marketing team:

- **AI tools:** creatives, analytics, testing;
- **ad platforms:** Meta, Google, TikTok, Apple, AppsFlyer;
- **agents and models:** new models, MCP, automation cases.

The scout checks every pick against a primary source: the company website, a changelog, a repository. Search summaries regularly describe products that do not exist, so the report ends with a "Did not pass the check" block.

## Who it is for

For founders and marketing teams who have no time to follow every release in AI and advertising. It is tuned for B2C with paid acquisition: mobile apps, fintech, e-commerce. If your product is different, describe it in the CONTEXT block and the scout will change its selection.

## Why I built it

For myself. There are so many AI and advertising releases that reading them would take half of my week. And search summaries confidently describe products that do not exist: once the search results all described a Meta video product with a price and features, and it was not real. I needed a filter that brings a few things, but verified ones, and says right away what to do with them.

I use it myself. This is a version for you: without my context, with a place for yours.

[Anna Vetrinskaya](https://vetrinskaya.com), growth co-founder

## How to start (3 minutes)

Any AI assistant that can search the web and run scheduled tasks will work: ChatGPT, Gemini, Perplexity, Claude. The scout is plain text with no code, so it is not tied to one service.

1. Open [`SKILL.en.md`](SKILL.en.md) and copy all the text.
2. Fill in the CONTEXT block: product, markets, channels, team, what matters most right now. The more precise it is, the less noise in the report.
3. Paste the text into a chat with your assistant and add:
   > Run this instruction every Monday at 9:00.
4. Ask it to run once right away to see the first report.

Where to set it up:

- **ChatGPT:** Tasks. The report comes as a notification.
- **Gemini:** Scheduled actions.
- **Perplexity:** Tasks. Perplexity search is strong, which is good for a scout.
- **Claude:** scheduled tasks in the desktop app, see below.

Scheduled tasks usually need a paid plan. I use the scout in Claude myself, so it is tested best there.

## If you use Claude

In [Claude](https://claude.ai/download) you do not need to copy the text. You can give it the whole file:

1. Download [`SKILL.en.md`](SKILL.en.md) and fill in the CONTEXT block.
2. Open Claude, attach the file and write:
   > Create a scheduled task from this file: every Monday at 9:00.
3. Ask Claude to run the task once right away.

The report appears in the task's run history. You need a Pro plan or higher and the desktop app (Cowork or Claude Code), or Claude Code in the terminal.

## If you build your own automations

In n8n or Make, set the scout up as a chain of "schedule → model with web search → Telegram or email". The text of `SKILL.en.md` goes into the model instruction. Remove step 5 from it: the chain handles delivery.

## How to adjust it

- **Topics and sources** are edited in steps 1–2 of `SKILL.en.md`.
- **Rhythm.** You can run the scout every day. Then replace "7 days" with "1–2 days" in step 1.
- **Language.** For a report in another language, change the line "Write in English" in step 4. A Russian version of the scout is in [`SKILL.md`](SKILL.md).

## Report in Telegram (optional)

This section is for people whose assistant runs commands on their own computer: Claude Code in the app or in the terminal. You do not need it in ChatGPT, Gemini or Perplexity: they run on their own servers, and the report comes through their notification. Do not paste a bot token there: they cannot send the message, and the token will stay in the chat history.

A bot token is a password. It is stored in the macOS Keychain, not in files. All commands below are typed in the Terminal app.

1. Create a bot with [@BotFather](https://t.me/BotFather) and copy the token.
2. Save the token in the Keychain. The command asks you to paste the token twice, and it does not show it on screen:
   ```bash
   security add-generic-password -a "$USER" -s ai-scout-tg-token -w
   ```
3. Send any message to your bot in Telegram. Then find your chat id:
   ```bash
   T=$(security find-generic-password -s ai-scout-tg-token -w) && curl -s "https://api.telegram.org/bot${T}/getUpdates" | grep -o '"chat":{"id":[0-9-]*' | head -1
   ```
   The answer is a line like `"chat":{"id":123456789`. The number at the end is your chat id.
4. Save the chat id the same way, under a different name:
   ```bash
   security add-generic-password -a "$USER" -s ai-scout-tg-chat -w
   ```

Done. On the next run the scout takes the token from the Keychain and sends the report. On first access macOS may ask for permission: run the scout once by hand and click "Always Allow", or a scheduled run will stop at that window.

Do not paste the token into `SKILL.en.md` or into a chat with the assistant, and do not publish it in a repository.

**Windows and Linux.** There is no Keychain there. Set the environment variables `TELEGRAM_BOT_TOKEN` and `TELEGRAM_CHAT_ID` with your system tools, and the scout will use them. Do not put the token into project files.

## Want more

The scout is one of the modules of [Marketing Shared Brain](https://vetrinskaya.com/#formats): a shared marketing memory for a team and AI agents. If you need agents like this built into your marketing, [tell me about your project](https://vetrinskaya.com/brief).

License: MIT
