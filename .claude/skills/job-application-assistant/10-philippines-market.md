---
framework_version: 1.0.0
---

# Philippine Market Guide

<!-- PH fork addition. Read this whenever the candidate is based in the Philippines or a
posting is for a Philippine employer or a foreign employer hiring Philippine-based staff.
It adjusts evaluation, CV, cover letter, salary and interview advice; the framework rules
in the other files still apply. Laws and rates change - when a figure decides a
recommendation, verify it with a current official source (DOLE, BIR, SSS, PhilHealth,
Pag-IBIG, DMW) per 09-web-research.md before stating it. -->

## Two kinds of roles - evaluate them differently

| | Local employer (PH company, BPO, PH branch of a multinational) | Foreign employer, remote from PH |
|---|---|---|
| Contract | Employee under the Labor Code, often 6-month probation then regular | Usually independent contractor, sometimes via an Employer of Record (Deel, Remote, Oyster, etc.) |
| Pay | Monthly PHP, **gross** (before tax and contributions) | Monthly or hourly, usually USD; often paid via Wise, Payoneer, Deel |
| Benefits | 13th month pay, SSS/PhilHealth/Pag-IBIG, HMO, leave credits | Usually none unless via an EOR - you fund your own SSS (voluntary), PhilHealth, Pag-IBIG, HMO |
| Tax | Withheld by employer | Contractor files and pays own taxes with BIR (register as self-employed/professional) |
| Hours | Day shift or BPO night shift | Often overlaps US/EU/AU hours - check the required working window |

When scoring fit (`04-job-evaluation.md`), treat these as different packages: compare a
contractor USD rate against a local salary only after accounting for the missing 13th
month, HMO, paid leave and employer contributions. A rough rule: a contractor rate should
be noticeably higher than the local gross salary you'd accept, not equal to it.

## Location tiers (fill in `search-queries.md`)

Common hubs for tech and office work:
- **Metro Manila:** Makati, BGC/Taguig, Ortigas (Pasig/Mandaluyong), Quezon City (Eastwood, Vertis North, UP-Ayala TechnoHub), Alabang (Muntinlupa), Manila, Pasay/Bay Area, Parañaque
- **Outside NCR:** Cebu City / Cebu IT Park, Clark (Pampanga), Laguna and Cavite (CALABARZON), Iloilo, Bacolod, Davao, Baguio
- Commute in Metro Manila is measured in time, not distance: a 10 km trip can take 1-2 hours at rush hour. When the candidate states a commute limit, judge hybrid/onsite postings by realistic travel time, and treat "onsite 5 days" in a far city as a strong negative.
- "Remote - Philippines" on LinkedIn often means a foreign company hiring PH-based contractors; read the posting for the employer's country and working hours.

## Job boards

| Board | Best for | Shipped CLI? |
|---|---|---|
| LinkedIn (`linkedin-search`, `-l "Philippines"` or `-l "Metro Manila"`) | Local + multinational + remote | Yes |
| freehire (`freehire-search --country PH` or `--remote remote --region apac,global`) | Tech roles, remote | Yes |
| JobStreet (ph.jobstreet.com) | Largest local general board | No - WebSearch fallback, or `/add-portal` |
| Kalibrr (kalibrr.com) | Tech, startups, fresh grads | No - WebSearch fallback, or `/add-portal` |
| Indeed PH (ph.indeed.com) | Broad local coverage | No - WebSearch fallback |
| OnlineJobs.ph | Remote work for foreign (mostly US/AU) clients | No - WebSearch fallback |
| Bossjob (bossjob.ph) | Local, chat-first recruiting | No - WebSearch fallback |
| PhilJobNet (philjobnet.gov.ph) | DOLE government job portal | No - WebSearch fallback |

Some of these boards block automated access or require login; `/add-portal` declines
auth-walled portals. If a posting URL can't be fetched, ask the user to paste the text.

## Red flags and scams (check before every application)

Flag in the evaluation, prominently, if a posting or recruiter:
- Asks the applicant to **pay** anything: "processing fee", training fee, uniform, medical, "placement fee" for a local job, or a laptop deposit
- Recruits only via Telegram/WhatsApp/Viber with no company domain email, or offers pay for "liking videos", "rating products", or "tasks" (common task scam)
- Wants SSS, TIN, bank details or ID photos **before** an interview or written offer
- Offers overseas (OFW) work: verify the agency's license with the **DMW** (Department of Migrant Workers) before proceeding
- Pays a "salary" far above market for an entry-level remote role with no interview

## CV conventions

Local Philippine resumes traditionally include a photo, birthdate, age, civil status,
height/weight, religion and a "character references" list. **Default to the international
format the framework already uses** (no photo, no personal statistics):
- RA 10911 (Anti-Age Discrimination in Employment Act) prohibits employers from requiring age or birthdate in applications, so leaving them out is normal and safe.
- The Data Privacy Act (RA 10173) makes over-sharing personal data unnecessary; it also gives the candidate grounds to decline sensitive questions.
- **Never put government ID numbers on a CV:** SSS, TIN, PhilHealth, Pag-IBIG, UMID, passport, PhilSys. Employers collect these after an offer.
- Add a photo or personal details only if the user says a specific local employer explicitly requires them.
- Address: city and province is enough (e.g. "Quezon City, Metro Manila"). Phone in `+63 9XX XXX XXXX` format.
- English is the standard CV language for PH professional and tech roles. Keep `CV language: English` unless the user asks otherwise.
- Licensure exams (PRC board passer, e.g. "Licensed Electronics Engineer, PRC 2022"), Civil Service eligibility and Latin honors (cum laude, magna cum laude) are valued locally - include them when true.
- TESDA National Certificates (NC II etc.) count as certifications.
- Fresh grads: OJT/internship and capstone/thesis projects belong under experience or projects.

## Cover letter conventions

- Write in English unless the posting is in Filipino.
- Address the named recruiter if known; otherwise "Dear Hiring Manager," - never "Dear Sir/Madam".
- Closings: "Sincerely," or "Best regards," for private companies and foreign employers; "Respectfully yours," for government and very formal local employers.
- Many local applications go through JobStreet/Kalibrr forms or email; a short email-body version of the cover letter is often more useful than a PDF. Offer both.
- For foreign remote roles, state availability for the employer's working hours (e.g. "available to work US Eastern hours") and a reliable work setup (internet with backup, power backup) - these are real screening criteria.

## Salary and offer evaluation

- Local salaries are quoted **monthly, gross, in PHP** (e.g. "₱45,000-60,000/month"). Always say "gross monthly" when giving numbers. Ask whether a range is gross or take-home if unclear.
- "Expected salary" is a standard form field and interview question. Help the user give a researched range, not a single number, and never below what they'd accept.
- Total package checklist for a local offer: basic pay, 13th month pay (mandatory for rank-and-file, PD 851), HMO coverage (and for how many dependents), allowances (rice, transport, internet, de minimis), leave credits (Service Incentive Leave is the legal minimum; many employers give more VL/SL), performance bonus, night differential for night shift (legal minimum is an extra 10% for 10 PM-6 AM), WFH/hybrid arrangement, shuttle or transport.
- Probation is usually up to 6 months; regularization is when many benefits start - note this in the evaluation.
- Resignation notice under the Labor Code is generally 30 days; factor the user's current notice period into start dates.
- For contractor roles: ask about rate currency, payment method and fees, paid time off (usually none), equipment, and hours. Remind the user they must register with BIR and handle their own contributions; suggest checking a tax professional for their case.
- Salary data sources for `salary_data.json` (`tools/README_SALARY_TOOL.md`): JobStreet salary insights, Kalibrr, Glassdoor/PayScale PH, recruiter salary guides (e.g. Robert Walters, Michael Page, Hays Philippines), and the user's own offers. Record the currency (PHP or USD) in `metadata`.

## Interview process norms

Typical local flow: HR/recruiter screening call → assessment (aptitude, technical test or
take-home) → technical/hiring-manager interview → final interview (department head) → job
offer → pre-employment requirements (NBI clearance, medical exam, government IDs, TIN,
SSS, PhilHealth, Pag-IBIG numbers, sometimes a background check).

When preparing interviews (`07-interview-prep.md`), also prepare the user for:
- "Tell me about yourself" (almost always first), "Why are you leaving your current job?", "What is your expected salary?", "When can you start?"
- BPO and foreign-client roles: questions about night shift, working hours and internet setup
- Foreign remote roles: a paid trial task or a time-zone overlap check is common
