# Agent Wiki Schema

## Purpose

This wiki is built for agents, not humans. It compiles operational knowledge from daily updates into structured articles. Agents read this wiki before pulling live data.

## Owner

Yana, Digital Marketing Executive, Justlife. UAE.
Primary source channel: D02E7Q76T2T

## Article format

Every article must start with YAML frontmatter:

```yaml
---
summary: one sentence
status: Active | Stale | Resolved | Monitoring
last_updated: DD.MM.YYYY
---
```

Then content. Then a **Backlinks** section at the bottom listing related articles.

## Content rules

* Write decisions, not discussions. If something was discussed but not decided, mark it [OPEN].
* Write in present tense for current status, past tense for decisions already made.
* Include numbers wherever they appear in the source (utilization %, revenue, CPA, etc).
* Every person mentioned in an article gets a backlink to their people/ article.
* Every experiment mentioned gets a backlink to its experiments/ article.

## Reading the wiki (Step 0)

Load state.md first. This single file contains: CRITICAL/URGENT/HIGH items, workstream statuses, full open items table, active experiments, people watch list, and key metrics.

Only fetch individual workstream or people files if state.md lacks enough detail for the current task. Fetch minimum necessary. Do not fetch files speculatively.

## Ingest workflow (for updates)

After any agent run that produces new decisions, open items, or status changes:
1. Regenerate state.md completely from the current synthesis (full rewrite, never append).
2. Append new decisions to decisions/log.md.
3. Update index.md last_updated and any status summaries that changed.
4. Update individual workstream or people files only where something actually changed.
5. Write reports/DD.MM.YYYY.md for the day if running a daily briefing.

state.md rules:
- Tables only. No prose.
- CRITICAL = hard deadline 24-48h. URGENT = action this week. HIGH = track closely.
- Remove resolved items every cycle. Do not carry completed items forward.
- Days Open increments by 1 daily. Reset to 0 on resolution.
- Metrics: known values only. No placeholders.

## Staleness rule

Articles not updated in 7+ days: add [STALE] tag to their entry in index.md.

## What belongs here

Decisions made (not just discussed). Experiment outcomes with numbers. People: ownership areas, open items, working patterns. Workstream status: current state, blockers, next step. Metric definitions and benchmarks. state.md: compressed current state snapshot, regenerated daily by the briefing agent.

## What does not belong here

Raw meeting transcripts. Day-by-day operational logs (those stay in your source channels). Live metrics that change daily. Credentials or secrets.
