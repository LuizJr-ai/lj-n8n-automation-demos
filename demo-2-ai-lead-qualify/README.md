<!-- readme-type: demo -->
# 🧠 Demo 2 — AI Lead Qualifier → Route Hot Leads

> Score an incoming lead with AI, record every lead, and route the hot ones to the team instantly.

## 🚀 What It Does
1. A lead arrives via **Webhook** (`Receive Lead (POST)`).
2. **Normalize Lead Fields** (Set) maps the raw form into a clean contract.
3. **Qualify Lead (AI)** scores it 0–100 and assigns a tier (`hot` / `warm` / `cold`) with reasoning, using a **structured output parser** (`Lead Score Schema`). The chat model is **swappable** (Groq by default).
4. **Validate & Guard Output** (Code) enforces a valid score/tier — falls back to `review` if the AI output is malformed.
5. **Google Sheets** records every lead + score + tier.
6. **Route: Hot vs Rest** (IF) sends hot leads to **Telegram** (owner) and **Slack** (team); the rest are just recorded.

## ⚙️ Nodes & Credentials
| Node | Purpose | Credential |
|------|---------|------------|
| Receive Lead (POST) (Webhook) | Receives the lead | — |
| Normalize Lead Fields (Set) | Clean/map fields | — |
| Qualify Lead (AI) + Lead Score Schema | Score/classify with structured output | — |
| Chat Model — swappable | LLM backing the qualifier | Groq API (or any chat model) |
| Validate & Guard Output (Code) | Enforce valid score/tier | — |
| Save Lead to Google Sheet | Persist every lead | Google Sheets OAuth2 |
| Route: Hot vs Rest (IF) | Branch by tier | — |
| Alert Owner (Hot Lead) — Telegram | Alert on hot lead | Telegram bot |
| Notify Team (Slack) | Post hot lead to channel | Slack API |

## 📥 How to Import & Configure
1. `Import from File` → `workflow.json`.
2. **AI model:** connect your Groq (or other) chat-model credential — the model node is swappable.
3. **Google Sheets:** connect your OAuth2 credential and point to your target spreadsheet/sheet.
4. **Telegram:** connect your bot and set `chatId` (placeholder: `<YOUR_TELEGRAM_CHAT_ID>`).
5. **Slack:** connect your credential and set the destination channel.
6. **Tally/form:** copy the Webhook URL into your form's webhook integration.
7. Send a test lead, confirm a clean run, then **activate**.

## 📦 Files
- `workflow.json` — importable workflow (sanitized: no personal IDs/secrets)
- `demo.gif` — the flow running
