<!-- readme-type: demo -->
# 🎯 Demo 1 — Lead Capture → Sheet + Instant Alerts

> Turn a web form submission into a new spreadsheet row and instant alerts to the team — in real time.

## 🚀 What It Does
1. A **Tally** form submission hits the **Webhook**.
2. **Parse + Clean Lead Data** (Code) normalizes the fields (name, email, phone, company, message).
3. **Google Sheets** appends the lead as a new row.
4. Instant alerts fire to **Telegram** (owner) and **Slack** (team channel).

## ⚙️ Nodes & Credentials
| Node | Purpose | Credential |
|------|---------|------------|
| Form Submission - Tally (Webhook) | Receives the form POST | — |
| Parse + Clean Lead Data (Code) | Normalize/clean fields | — |
| Save Lead to Google Sheets | Append lead row | Google Sheets OAuth2 |
| Notify Owner - Telegram | Instant owner alert | Telegram bot |
| Notify Team (Slack) | Post to team channel | Slack API |

## 📥 How to Import & Configure
1. `Import from File` → `workflow.json`.
2. **Google Sheets:** connect your OAuth2 credential and point the node to your target spreadsheet/sheet.
3. **Telegram:** connect your bot credential and set `chatId` (placeholder: `<YOUR_TELEGRAM_CHAT_ID>`).
4. **Slack:** connect your credential and set the destination channel (default `n8n-leads`).
5. **Tally:** copy the Webhook URL from the Webhook node into your Tally form's webhook integration.
6. Send one test submission, confirm a clean run, then **activate**.

## 📦 Files
- `workflow.json` — importable workflow (sanitized: no personal IDs/secrets)
- `demo.gif` — the flow running
