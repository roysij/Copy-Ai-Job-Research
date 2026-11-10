# Search Queries for Job Scraper

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`; Danish demos and any skill you add with `/add-portal` are included the same way. You do **not** need a matching `site:` line below for those CLIs to run.

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails.

**Language scope:** write every query category in every language listed in your CLAUDE.md Languages table (typically 1-2, sometimes more). A posting requiring a language you have *not* declared, as a job condition, is excluded before scoring; a posting requiring a *higher level* than you declared in a language you *do* work in is flagged for your own judgment, not excluded — see `04-job-evaluation.md`'s Language Gate, the single source of truth for this rule. Translate each category's keywords rather than machine-translating word-for-word (e.g. "Frontend Developer" -> "Desarrollador Frontend", not a literal word-for-word translation) if you work in more than one language.

## Search Sites

Market: **Philippines** (local roles + remote roles open to PH-based candidates). See `.claude/skills/job-application-assistant/10-philippines-market.md` for board notes and scam checks.

Primary (CLIs - run these first):
- **linkedin.com/jobs** via `linkedin-search` - run with `-l "Philippines"` (and `-l "[YOUR_CITY], Philippines"` for local roles); for remote roles also run with `--remote remote`
- **freehire.me** via `freehire-search` - tech roles; run with `--country PH`, and for remote with `--remote remote --region apac,global,none`

Primary (WebSearch `site:` fallback - no CLI yet; scaffold one with `/add-portal` on your own machine if you want structured results):
- **ph.jobstreet.com** - largest general Philippine job board
- **kalibrr.com** - tech, startups, fresh grads
- **ph.indeed.com** - broad local coverage
- **onlinejobs.ph** - remote work for foreign (mostly US/AU) clients

Secondary:
- **bossjob.ph**, **philjobnet.gov.ph** (DOLE) - optional local boards
- Direct Google searches with `site:` filters for known target companies' career pages

## Portal CLI location flags (Philippines)

```
bun run .agents/skills/linkedin-search/cli/src/cli.ts search -q "[YOUR_PRIMARY_JOB_TITLE_1]" -l "Philippines" --jobage 14 --format json
bun run .agents/skills/linkedin-search/cli/src/cli.ts search -q "[YOUR_PRIMARY_JOB_TITLE_1]" -l "Philippines" --remote remote --jobage 14 --format json
bun run .agents/skills/freehire-search/cli/src/cli.ts search -q "[YOUR_PRIMARY_JOB_TITLE_1]" --country PH --jobage 14 --format json
bun run .agents/skills/freehire-search/cli/src/cli.ts search -q "[YOUR_PRIMARY_JOB_TITLE_1]" --remote remote --region apac,global,none --jobage 14 --format json
```

For remote results, keep a posting only if it says it hires in the Philippines, APAC, or worldwide. Drop "Remote (US only)", "must be authorized to work in the US/EU" and similar.

## Query Categories

Queries are grouped by priority. Write **each category in every language from your Languages table** (see Language scope above). Combine each query with your location terms (e.g. your city, region, or metro area) where the site supports it.

Each priority has two kinds of block. **Plain terms** blocks are what the portal CLIs consume: one term per line, one CLI call per term, no `OR`, no `site:` prefix, and no location (the CLI's location flag, or the city in `--query` where that portal's SKILL.md says so, carries it). Quote a multi-word phrase only if the portal's `Query syntax:` line says quoting is honoured. **WebSearch-only** blocks are Google syntax (`site:`, quotes, `OR`) for the fallback path and are never passed to a CLI.

**Organize by function, not job title.** The same underlying work carries different titles across companies and markets (a "Data Scientist" role at one employer may be posted as "Insights Analyst" or "Data Consultant" at another). Name each priority category after the function it covers, and list several plausible job titles as query variants within that category rather than betting an entire priority tier on one exact title string.

### Priority 1: [YOUR_PRIMARY_ROLE_TYPE]

These match your strongest and most desired career direction.

#### Plain terms (portal CLIs)

```
[YOUR_PRIMARY_JOB_TITLE_1]
[YOUR_PRIMARY_JOB_TITLE_2]
[YOUR_KEY_SKILL]
```

#### WebSearch-only (`site:` fallback)

```
site:ph.jobstreet.com "[YOUR_PRIMARY_JOB_TITLE_1]" [YOUR_CITY]
site:ph.jobstreet.com "[YOUR_PRIMARY_JOB_TITLE_2]" [YOUR_CITY]
site:ph.jobstreet.com "[YOUR_KEY_SKILL]" [YOUR_CITY]
site:linkedin.com/jobs "[YOUR_PRIMARY_JOB_TITLE_1]" Philippines
site:kalibrr.com "[YOUR_PRIMARY_JOB_TITLE_1]"
site:ph.indeed.com "[YOUR_PRIMARY_JOB_TITLE_1]" [YOUR_CITY]
site:onlinejobs.ph "[YOUR_PRIMARY_JOB_TITLE_1]"
site:ph.jobstreet.com "[YOUR_PRIMARY_JOB_TITLE_1]" "work from home" OR remote
```

### Priority 2: [YOUR_DOMAIN_EXPERTISE]

These match your domain expertise.

#### Plain terms (portal CLIs)

```
[YOUR_DOMAIN_KEYWORD_1]
[YOUR_DOMAIN_KEYWORD_2]
```

#### WebSearch-only (`site:` fallback)

```
site:ph.jobstreet.com [YOUR_DOMAIN_KEYWORD_1] [YOUR_CITY] OR [YOUR_REGION]
site:ph.jobstreet.com [YOUR_DOMAIN_KEYWORD_2] Philippines
site:linkedin.com/jobs [YOUR_DOMAIN_KEYWORD_1] [YOUR_CITY] Philippines
```

### Priority 3: [YOUR_ADJACENT_ROLE_TYPE]

Adjacent roles you could pivot into.

#### Plain terms (portal CLIs)

```
[YOUR_ADJACENT_TITLE_1]
[YOUR_ADJACENT_TITLE_2]
```

#### WebSearch-only (`site:` fallback)

```
site:ph.jobstreet.com "[YOUR_ADJACENT_TITLE_1]" [YOUR_KEY_SKILL] [YOUR_CITY]
site:ph.jobstreet.com "[YOUR_ADJACENT_TITLE_2]" [YOUR_KEY_SKILL] [YOUR_CITY]
```

### Priority 4: Broader Technical / Consulting

Wider net for general technical roles.

#### Plain terms (portal CLIs)

```
[YOUR_KEY_SKILL] developer
technical consultant
```

#### WebSearch-only (`site:` fallback)

```
site:ph.jobstreet.com [YOUR_KEY_SKILL] developer [YOUR_CITY]
site:linkedin.com/jobs "[YOUR_KEY_SKILL] developer" [YOUR_CITY]
site:ph.jobstreet.com "technical consultant" [YOUR_DOMAIN] [YOUR_CITY]
```

## Location Filter

When evaluating results, check location and work arrangement together. In Metro Manila judge commute by realistic rush-hour travel time, not distance (see `10-philippines-market.md`).
- **Remote:** accept if the posting hires in the Philippines, APAC or worldwide; reject "US only" / "EU only" / work-authorization-restricted remote
- **Ideal (onsite/hybrid):** [YOUR_CITY] and nearby cities (e.g. Makati, BGC/Taguig, Ortigas, Quezon City, Alabang - keep only those within your commute)
- **Acceptable:** [ACCEPTABLE_AREA_1], [ACCEPTABLE_AREA_2] (hybrid only, or ~X min commute)
- **Borderline:** [BORDERLINE_AREA] (~X min each way)
- **Too far / relocation:** [TOO_FAR_AREA] (e.g. Cebu, Clark, Davao unless remote or you'd relocate); overseas onsite roles (verify the agency with DMW first)

## Language Filter

Your working languages and levels are in CLAUDE.md's Languages table. When filtering scraped results, apply `04-job-evaluation.md`'s Language Gate: a posting requiring a language you haven't declared at all is excluded; a posting requiring a higher level than you declared in a language you do work in is not excluded, flag it clearly instead (see `job-scraper/SKILL.md`'s Step 3 "Quick Fit Assessment" for how the flag surfaces in `/scrape` output). Postings simply *written* in a language you don't work in, that don't require it on the job, are fine.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
