# Bootstrap Prompt

Copy everything below the line into Claude Code to generate your wiki. Customize the sections marked with `<!-- CUSTOMIZE -->` before running.

---

You are doing a one-time bootstrap job. You will populate this repo with a structured knowledge wiki based on my operational history.

## STEP 1 — CONFIGURE

**Primary source:** Slack channel `D02E7Q76T2T`
**Date range:** Fetch all messages from `YYYY-MM-DD` onwards
**Source type:** Daily marketing briefings, campaign updates, performance reports, and standup notes

<!-- CUSTOMIZE: If not using Slack, replace Step 3 below with your data source.
Examples:
- "Read the last 30 messages from my Apple Notes"
- "Read the Google Doc at [URL]"
- "I'll paste my meeting notes below: [paste]"
-->

## STEP 2 — CREATE FOLDER STRUCTURE

```bash
mkdir -p workstreams people experiments decisions metrics
```

## STEP 3 — FETCH SOURCE MATERIAL

Use the Slack MCP tool to read channel `D02E7Q76T2T`. Fetch all messages using pagination until you have everything from your start date onwards. These are your source of truth. Do not invent or assume anything not explicitly stated in these messages.

## STEP 4 — CREATE ARTICLES

For each category below, extract everything relevant from the source history and write structured articles. Use only what appears in the source. Be specific. Include real numbers. Every article must have YAML frontmatter, content body, and a Backlinks section.

### Workstreams

**workstreams/paid-media.md** — Include: Google Ads and Meta Ads performance, spend vs budget, CPA by channel, active campaigns, ROAS trends, blockers, open items. Key people involved.

**workstreams/seo-organic.md** — Include: organic traffic trends, keyword rankings, content pipeline status, technical SEO issues, monthly targets. Key people involved.

**workstreams/social-media.md** — Include: platform performance (Instagram, TikTok, LinkedIn), engagement rates, follower growth, content calendar status, influencer partnerships. Key people involved.

**workstreams/crm-email.md** — Include: email campaign performance (open rate, CTR, conversions), CRM segmentation, automation workflows, retention metrics. Key people involved.

**workstreams/app-marketing.md** — Include: app install campaigns, ASO status, app store ratings, in-app conversion funnels, push notification performance. Key people involved.

**workstreams/content-creative.md** — Include: creative production pipeline, ad creative performance, content briefs in progress, approvals pending. Key people involved.

**workstreams/analytics-reporting.md** — Include: dashboard status, tracking/attribution issues, reporting cadence, data gaps. Key people involved.

### People

**people/[name].md** — Include: role, ownership areas, all open items assigned to them across all source messages, delivery patterns (items carried over multiple days), bandwidth flags.

<!-- Add one entry per team member or key stakeholder:
people/[agency-contact].md — Include: role (performance agency lead), ownership areas (paid media execution), open items, SLA patterns.
people/[designer].md — Include: role (creative/designer), ownership areas (ad creatives, social content), open items, turnaround times.
-->

### Experiments

**experiments/[name].md** — Include: hypothesis, mechanic (channel, audience, creative/offer variant), result with numbers (CTR, CPA, ROAS, conversion rate), status (Active / Resolved), next steps.

<!-- Examples of marketing experiments to document:
experiments/meta-broad-vs-lookalike.md — broad targeting vs lookalike audiences, CPA comparison
experiments/google-pmax-vs-search.md — Performance Max vs Search campaigns, ROAS and conversion volume
experiments/email-subject-line-test.md — personalized vs generic subject lines, open rate delta
experiments/app-install-creative-q2.md — video vs static creative, install cost and quality
-->

### Decisions Log

**decisions/log.md** — Format every entry as:

```
## DD.MM.YYYY

**Decision title**
What was decided, one to three sentences max. Source: [which message/meeting].
```

Extract every clear marketing or campaign decision from all source messages in chronological order.

### Metrics

**metrics/definitions.md** — Define every metric mentioned across all source messages. For each: name, definition as used at Justlife, current benchmark or target.

**metrics/weekly-benchmarks.md** — Extract every number mentioned as a target or threshold. Format as a table: Metric | Target/Threshold | Source | Date mentioned.

## STEP 5 — CREATE INDEX

Write `index.md` as a full catalog of every article created:

```markdown
# Wiki Index

Last updated: [today's date DD.MM.YYYY]
Source: Slack channel D02E7Q76T2T — Justlife Digital Marketing

## State
* [[state.md]] - Compressed current state snapshot. Load this at Step 0.

## Workstreams
* [[workstreams/paid-media]] - [one-line summary] | [status]
* [[workstreams/seo-organic]] - [one-line summary] | [status]
* [[workstreams/social-media]] - [one-line summary] | [status]
* [[workstreams/crm-email]] - [one-line summary] | [status]
* [[workstreams/app-marketing]] - [one-line summary] | [status]
* [[workstreams/content-creative]] - [one-line summary] | [status]
* [[workstreams/analytics-reporting]] - [one-line summary] | [status]

## People
* [[people/name]] - [one-line summary] | Active

## Experiments
* [[experiments/name]] - [one-line summary] | [status]

## Decisions
* [[decisions/log]] - Chronological log of all marketing decisions

## Metrics
* [[metrics/definitions]] - Metric definitions and benchmarks
* [[metrics/weekly-benchmarks]] - Current targets and thresholds
```

## STEP 6 — CREATE LOG

Write `log.md`:

```markdown
# Wiki Log

## [today's date] bootstrap

Initial wiki created from Slack channel D02E7Q76T2T (Justlife Digital Marketing), covering [date range].
Articles created: [count per folder]. Source messages processed: [count].
```

## STEP 7 — GENERATE state.md

Using all articles you just created, generate the initial state.md. This is a compressed snapshot of current state for token-efficient loading.

Populate:
- CRITICAL/URGENT/HIGH sections: extract any campaign deadlines, budget pacing issues, or urgent blockers from the source
- Workstream Status table: one row per workstream article created
- Open Items table: every open item across all workstream and people articles
- Active Experiments: any experiment with status Active or Pending decision
- People Watch List: people with open items assigned to them
- Key Metrics: every metric with a current known value from metrics/weekly-benchmarks.md (e.g. CPA, ROAS, CTR, CAC, app installs, email open rate)

state.md is always a full rewrite. Generate it fresh from the wiki you just built.

## STEP 8 — COMMIT AND PUSH

```bash
git add .
git commit -m "bootstrap: initial wiki from Slack D02E7Q76T2T [date range]"
git push -u origin main
```

## STEP 9 — FINAL OUTPUT

After pushing, print:
1. GitHub repo URL (https://github.com/yanabautista-beep/Yana-Wiki)
2. Article count per folder
3. Any gaps where source data was thin or missing
4. The raw base URL for fetching articles: `https://raw.githubusercontent.com/yanabautista-beep/Yana-Wiki/main/`
5. The Step 0 line to add to your agent prompts, with the real index.md URL
