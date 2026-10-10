<!-- readme-type: index -->
# 🤖 n8n Automation Demos

> Three self-contained n8n workflows for small-business automation: import one, connect your own credentials, and it runs.

![n8n compatible](https://img.shields.io/badge/n8n-compatible-EA4B71)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow)
![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen)

Each demo ships a README, a recording of it running and an importable `workflow.json`. The exports are
sanitized: no credentials, credential ids, personal hosts, chat ids or document ids are committed.

## 📦 What's Inside
| Demo | What it does | Core nodes |
|------|--------------|------------|
| [🎯 Lead Capture](demo-1-lead-capture) | Form lead → spreadsheet row + instant alerts | Webhook · Code · Google Sheets · Telegram · Slack |
| [🧠 AI Lead Qualifier](demo-2-ai-lead-qualify) | Score a lead with AI → route hot leads → record every lead | Webhook · AI Agent · Code · Google Sheets · IF · Telegram · Slack |
| [📰 Content Digest](demo-3-content-digest) | Scheduled AI news digest of RSS feeds → your inbox | Schedule · RSS · AI · Gmail |

## ✅ Requirements
- An **n8n** instance (self-hosted or cloud).
- Credentials for the services a demo uses (Google, Telegram, Slack, an AI provider, Gmail).

## 🚀 Quick Start
1. **Import** — in n8n, `Import from File` → pick the demo's `workflow.json`.
2. **Connect credentials** — each demo's README lists exactly which ones (Google Sheets, Telegram, Slack, AI provider, Gmail).
3. **Replace placeholders** — e.g. `<YOUR_TELEGRAM_CHAT_ID>` (Demo 1/2), the feed list and recipient (Demo 3).
4. **Wire the trigger** — for form demos, paste the Webhook URL into your form (e.g. Tally); for Demo 3, set the schedule.
5. **Run once** — trigger a test, confirm a clean execution, then **activate**.

## 🧭 Design Principles
- Few nodes, clear purpose — over node soup.
- No secrets committed: credentials ship as empty references + placeholders.
- Real input first: every field is mapped against the actual payload, never an assumed shape.
- Inactive until proven: each workflow ships after at least one clean end-to-end run.

## 📂 Repository Layout
```
demo-1-lead-capture/     workflow.json · README.md · demo.gif
demo-2-ai-lead-qualify/  workflow.json · README.md · demo.gif
demo-3-content-digest/   workflow.json · README.md · demo.gif
```

## 📄 License
MIT — see [`LICENSE`](LICENSE). Contributions and issues welcome.

## 👤 Author
Built by **Luiz Jr** as part of a hands-on portfolio in AI orchestration & n8n automation.
