# Philippine setup (this copy)

This private copy of [ai-job-search](https://github.com/ai-job-search-dev/ai-job-search) is set up for a job seeker based in the Philippines. Upstream updates merge in daily via `.github/workflows/sync-upstream.yml`.

## What's different from upstream

| File | Change |
|---|---|
| `.claude/skills/job-application-assistant/10-philippines-market.md` | **New.** Local vs foreign-remote roles, PH job boards, scam checks, CV norms (no photo/age/government IDs), cover letter closings, PHP gross monthly salary + 13th month/HMO offer checklist, contractor tax note, interview flow |
| `CLAUDE.md` | Location set to Philippines, English + Filipino in the Languages table, a pointer to the market guide |
| `.claude/skills/job-scraper/search-queries.md` | LinkedIn/freehire run with Philippines flags; JobStreet, Kalibrr, Indeed PH, OnlineJobs.ph as WebSearch fallbacks; Metro Manila commute tiers; remote filter (drops "US only") |
| `.claude/commands/setup.md` | `/setup` keeps the Philippine boards and asks local vs remote vs both |
| `salary_lookup.py` | Matches company names with Inc./Corp./Corporation/Philippines suffixes |

Danish portals stay disabled (upstream default).

## Getting started

1. Install Claude Code, Python 3.10+, Bun and LaTeX (MiKTeX on Windows) - see `SETUP.md`.
2. `python tools/install_portal_clis.py`
3. Run `claude`, then `/setup`. When asked about location, answer with your city and whether you want local roles, remote roles, or both.
4. `/scrape` to find jobs, `/apply <url or pasted posting>` to apply.

## Optional: structured JobStreet / Kalibrr search

These boards are searched through Google `site:` queries by default. For structured results, run `/add-portal` on your own machine and give it `https://ph.jobstreet.com` or `https://www.kalibrr.com`. It tests the portal live before registering it. Some boards block automated access; if so, the `site:` fallback keeps working.

## Keeping updates clean

The Philippine changes are kept small so the daily upstream merge rarely conflicts. Your personal data (from `/setup`) will differ from upstream's placeholders; if a merge ever conflicts, the sync opens an issue with instructions.
