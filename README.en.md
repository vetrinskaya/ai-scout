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

## What you need

Any AI assistant that can search the web and run scheduled tasks. The scout is plain text with no code, so it is not tied to one service. I tested it in [Claude](https://claude.ai/download), and the instructions below start there. Other options are in the "Not using Claude?" section.

## How to set it up in Claude (5 minutes)

1. Download [`SKILL.en.md`](SKILL.en.md).
2. Open it and fill in the CONTEXT block: product, markets, channels, team, what matters most right now. The more precise it is, the less noise in the report.
3. Open Claude, attach the file and write:
   > Create a scheduled task from this file: every Monday at 9:00.
4. Ask Claude to run the task once right away to see the first report.

The report appears in the task's run history. You need a Pro plan or higher and the desktop app (Cowork or Claude Code), or Claude Code in the terminal.

## Not using Claude?

Copy the text of `SKILL.en.md` (after you fill in CONTEXT) and set it up as a scheduled task where it is convenient for you:

- **ChatGPT:** Tasks. Ask: "Run this instruction every Monday at 9:00." The report comes as a notification.
- **Gemini:** Scheduled actions, the same way.
- **Perplexity:** Tasks. Perplexity search is strong, which is good for a scout.
- **n8n or Make:** a chain of "schedule → model with web search → Telegram or email".

Step 5 about Telegram will not work in these services, because it needs command-line access. The report comes through their own notification. Scheduled tasks usually need a paid plan.

## Report in Telegram (optional)

1. Create a bot with [@BotFather](https://t.me/BotFather) and copy the token.
2. Send any message to your bot. Then open `https://api.telegram.org/bot<TOKEN>/getUpdates` and find `"chat":{"id":...}`: this is your chat id.
3. Add both variables to `~/.claude/settings.json`:
   ```json
   {
     "env": {
       "TELEGRAM_BOT_TOKEN": "your token",
       "TELEGRAM_CHAT_ID": "your chat id"
     }
   }
   ```
   Keep the token only there: do not paste it into `SKILL.en.md` and do not publish it in a repository.

## How to adjust it

- **Topics and sources** are edited in steps 1–2 of `SKILL.en.md`.
- **Rhythm.** You can run the scout every day. Then replace "7 days" with "1–2 days" in step 1.
- **Language.** For a report in another language, change the line "Write in English" in step 4. A Russian version of the scout is in [`SKILL.md`](SKILL.md).

## Want more

The scout is one of the modules of [Marketing Shared Brain](https://vetrinskaya.com/#formats): a shared marketing memory for a team and AI agents. If you need agents like this built into your marketing, [tell me about your project](https://vetrinskaya.com/brief).

License: MIT
