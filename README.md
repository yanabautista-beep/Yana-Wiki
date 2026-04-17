# Yana's Marketing Wiki — Justlife

A structured knowledge base built for AI agents. This wiki compiles digital marketing operational knowledge — campaign decisions, experiment results, channel performance, and team ownership — into structured articles that an AI agent can read, reference, and update.

**Owner:** Yana, Digital Marketing Executive, Justlife, UAE
**Primary source:** Slack channel `D02E7Q76T2T`

## What this is

Marketing knowledge lives in Slack threads, campaign dashboards, and team calls. Decisions get made, campaigns launch, experiments run — and the context disappears as threads scroll past. This wiki captures that knowledge in a structured format so agents can act on it without re-fetching everything from scratch every time.

The wiki is designed to be:
- **Read by agents** as context before briefings, campaign analysis, or planning
- **Updated by agents** as new decisions and campaign results come in
- **Auditable by humans** when you need to check what was decided and when

## How it works

```
Slack channel D02E7Q76T2T (daily updates, campaign notes, decisions)
        ↓
  Bootstrap prompt (one-time, run with Claude Code)
        ↓
  Structured wiki (this repo)
        ↓
  Agent reads wiki at Step 0 before pulling live data
        ↓
  Agent flags articles that need updating
        ↓
  Ingest workflow keeps wiki current
```

## Token efficiency

The core pattern is state.md as a compressed snapshot layer.

Without state.md: agents fetch index.md + matching workstream files + people files at Step 0. On a mature wiki with 7+ workstreams, this costs 30-40K tokens per run before any live data is pulled.

With state.md: agents fetch one ~800-token file. Individual files are only fetched when a specific gap forces it. On the same wiki, Step 0 costs 800-1,500 tokens.

state.md is regenerated at the end of every briefing run. It is always current as of the last evening cycle. It is never manually edited.

## Quick start

### 1. Clone this repo

```bash
git clone https://github.com/yanabautista-beep/Yana-Wiki.git
cd Yana-Wiki
```

### 2. Customize the bootstrap prompt

Open `BOOTSTRAP.md`. It is already configured for your Slack channel and digital marketing workstreams. Add or remove workstreams and people to match your current team structure before running.

### 3. Run the bootstrap

Open Claude Code in your wiki directory and paste the contents of `BOOTSTRAP.md`. The agent will:

1. Fetch messages from Slack channel `D02E7Q76T2T`
2. Create articles for each workstream, person, experiment, and decision
3. Build the index and decision log
4. Generate state.md
5. Commit and push to GitHub

### 4. Connect to your workflows

Add this as Step 0 in any agent prompt that needs marketing context:

```
Step 0 — Wiki context: Fetch state.md from https://raw.githubusercontent.com/yanabautista-beep/Yana-Wiki/main/state.md
This file contains current open items, channel statuses, active experiments, team watch list,
and key marketing metrics. Use it as your baseline before pulling live data.

Only fetch individual workstream or people files if state.md lacks enough detail for today's task.
Fetch minimum necessary.

Regenerate state.md completely after every agent run that produces new decisions or status changes.
```

## Folder structure

```
Yana-Wiki/
├── CLAUDE.md              # Agent schema — rules for reading and writing articles
├── BOOTSTRAP.md           # One-time bootstrap prompt — already configured, run to populate
├── state.md               # Compressed state snapshot — load this at Step 0 (auto-regenerated)
├── index.md               # Article catalog with status tags (auto-generated)
├── log.md                 # Update log (auto-generated)
├── reports/               # Daily briefing reports (DD.MM.YYYY.md per day)
├── workstreams/           # Paid Media, SEO, Social, CRM, App Marketing, Content, Analytics
├── people/                # Team members and key stakeholders
├── experiments/           # A/B tests and campaign experiments with results
├── decisions/             # Chronological decision log
├── metrics/               # KPI definitions and benchmarks
└── templates/             # Article templates to reference
    ├── workstream.md
    ├── person.md
    ├── experiment.md
    └── metric.md
```

## Workstreams

| Workstream | What it tracks |
|---|---|
| Paid Media | Google Ads, Meta Ads — spend, CPA, ROAS, active campaigns |
| SEO & Organic | Traffic, rankings, content pipeline, technical issues |
| Social Media | Instagram, TikTok, LinkedIn — engagement, growth, content calendar |
| CRM & Email | Email performance, automation, retention, segmentation |
| App Marketing | Install campaigns, ASO, in-app funnels, push notifications |
| Content & Creative | Creative production, ad performance, approvals |
| Analytics & Reporting | Dashboards, attribution, tracking, data quality |

## Key metrics tracked

- **CPA** — Cost Per Acquisition by channel
- **ROAS** — Return on Ad Spend
- **CAC** — Customer Acquisition Cost
- **CTR** — Click Through Rate by channel and creative
- **App Installs** — Volume and cost per install
- **Email Open Rate / CTR** — Per campaign and automation
- **Organic Sessions** — Monthly trend and targets
- **Conversion Rate** — By channel and funnel stage

## Article format

Every article follows the same structure:

```markdown
---
summary: one sentence
status: Active | Stale | Resolved | Monitoring
last_updated: DD.MM.YYYY
---

# Title

Content body — decisions, numbers, current state.

## Backlinks

- [[related/article]]
```

## Keeping it current

### Manual updates
Edit articles directly when decisions are made. Update `index.md` if you add new articles. Append to `log.md`.

### Agent-powered updates (recommended)
Run "update the wiki from today's briefings" in Claude Code after your daily sync. The agent reads new Slack messages, identifies what changed, and updates the relevant articles.

## Staleness rule

Articles not updated in 7+ days get a `[STALE]` tag in `index.md`.

## Content rules

- **Write decisions, not discussions.** If something was discussed but not decided, mark it `[OPEN]`.
- **Write in present tense** for current status, past tense for decisions already made.
- **Include numbers** wherever they appear (CPA, ROAS, CTR, spend, installs, open rates).
- **Backlink everything.** Every person mentioned gets a link to their `people/` article. Every experiment gets a link to its `experiments/` article.

## What belongs here

- Campaign decisions made (not just discussed)
- Experiment outcomes with numbers
- People: ownership areas, open items, delivery patterns
- Channel status: current performance, blockers, next step
- Metric definitions and benchmarks

## What does not belong here

- Raw Slack transcripts
- Live dashboard data that changes daily
- Credentials, API keys, or secrets
- Day-by-day operational logs (those stay in Slack)
