<!-- readme-type: demo -->
# 📰 Demo 3 — Scheduled AI Content Digest

> On a weekly schedule, gather AI-news from multiple sources, curate and summarize them with an LLM, verify each story, and deliver a clean HTML digest to your inbox — with a safety gate that alerts you on Telegram if a run isn't good enough to send.

Branded as **AI Insight Weekly**. The header language follows an `outputLanguage` setting, so the same workflow can publish in English, Portuguese, etc.

## 🚀 What It Does
- **Schedule Trigger** fires once a week (default: Monday 10:00).
- Collects candidates from two source types: **RSS feeds** and **official sitemaps** (auto-discovers recent pages).
- **Deduplicates** against a **Data Table** so a story is never sent twice.
- **Ranks & balances** candidates across sources, keeps the top 30.
- Fetches each finalist's page as **evidence**, then an **LLM** (GPT-4o-mini) selects the edition and **writes one story per call** — a fan-out that guarantees the story count, with tolerant JSON parsing in Code (no rigid parser to break on).
- **Validates** the AI output (drops thin stories; fails safe if too few survive).
- **Safe-to-Send gate**:
  - ✅ pass → verify images (prefers `og:image`), build the HTML email, **send via Gmail**, then log the sent URLs to the Data Table.
  - ⚠️ fail → send a **Telegram failure alert** so you know the week's digest did not go out (no silent failures).

## ⚙️ Nodes & Credentials
| Node | Purpose | Credential |
|------|---------|------------|
| Schedule Trigger | Fire weekly | — |
| RSS Read / HTTP Request | Fetch feeds, sitemaps & page evidence | — |
| Data Table | Deduplicate + audit log of sent URLs | — |
| Code | Normalize, rank, validate, build email | — |
| AI (Chat Model, per-story fan-out) | Select edition & write each story | AI provider API key |
| IF — Safe to Send? | Quality gate | — |
| Gmail | Send the digest | Gmail OAuth2 |
| Telegram | Failure alert | Telegram bot |

## 📥 How to Import
1. `Import from File` → `workflow.json`.
2. Set your credentials (AI provider, Gmail, Telegram) and create the dedup **Data Table**.
3. Configure your sources, `outputLanguage`, recipient (`sendTo`) and Telegram chat ID.
4. Run once with the manual trigger, confirm a clean digest, then activate the schedule.

## 📦 Files
- `workflow.json` — importable, sanitized workflow
- `demo.gif` — the flow running
