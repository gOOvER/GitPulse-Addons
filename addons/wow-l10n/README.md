# WoW Addon Translator (`wow-l10n`)

GitPulse plugin for managing and translating World of Warcraft AddOns (`AceLocale-3.0`, `ns.L`, `tools/locale/*.json`) directly via GitHub.

## Features
- Scans WoW AddOn repositories including missing `L["..."]` key detection from Lua source files.
- Validates WoW placeholders (`%s`, `%d`, `%.1f`, `%1$s`), color codes (`|c...|r`), and texture tags (`|T...|t`).
- Optional AI suggestions (Gemini / OpenAI / Ollama) with a built-in WoW glossary.
- Exports `.lua` / `.json` files and opens 1-click GitHub Pull Requests.
