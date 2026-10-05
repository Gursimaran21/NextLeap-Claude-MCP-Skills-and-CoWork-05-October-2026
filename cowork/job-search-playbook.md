# Automating a job search with Claude Cowork

A practical playbook, not a promise. The goal is a **reproducible shortlist and application
pipeline**, with you approving anything that leaves your inbox.

> ⚠️ **Read this first.** Many job boards' terms of service prohibit automated scraping and
> bulk application. Automating *research* is broadly fine. Automating *applications* is where
> ToS risk lives — and some sites actively detect and ban it. Check each board's terms, keep
> volume human, and never misrepresent yourself. Everything below assumes you will review
> before anything is submitted.

---

## Why Cowork fits this

Job search is the archetypal Cowork task. It is multi-step, mostly independent per item,
touches the browser, produces files, and runs for a long time. That maps exactly onto what
Cowork was built for.

| Requirement | Cowork capability |
| --- | --- |
| Research many listings | Browser actions + web search |
| Produce a comparison artefact | Spreadsheet generation with working formulas |
| Track state across days | Projects — persistent files and memory |
| Run daily without you | Scheduled tasks (`/schedule`) |
| Stay on brand when writing | Skills + plugins |
| Fill forms on real sites | Built-in browser, or Claude in Chrome |

---

## Phase 1 — Set up a project

Create one Cowork **project** for the search. Give it a folder and a short instruction file.

```
job-search/
├── instructions.md
├── targets.md
├── companies/
├── applications/
└── tracker.csv
```

**instructions.md** — standing context, so you don't repeat yourself each session:

```markdown
# Job search — standing instructions

## What I want
[Role title] at [company size] companies, [location / remote].

## Hard filters — exclude if any fail
- Compensation below [X]
- Requires [X] years of [X]
- Industry in [list]

## Soft preferences
- [X] — nice to have, not disqualifying

## How to evaluate
Score 1–5 on: role fit, company quality, growth signal, comp, interview likelihood.
Drop anything scoring under [X].

## My voice for applications
- [Two or three sentences describing tone, e.g. "direct, no buzzwords, short sentences,
  one concrete example per claim"]
```

Cowork reads this every session in the project, so it stops re-deriving your criteria.

---

## Phase 2 — Research run

### First run — discovery

> Using `targets.md`, find [N] roles matching my hard filters. For each, record company,
> role title, link, comp if listed, and a one-line note on why it might fit. Save to
> `companies/discovery.csv` and tell me what you excluded and why.

**Review this before going further.** The exclusions matter more than the inclusions — if
Claude is cutting the wrong companies, every later stage is wasted.

### Second run — scoring

> Score every row in `companies/discovery.csv` against the criteria in `instructions.md`.
> Add columns for each score, a total, and a one-sentence justification per role. Sort by
> total. Flag anything where you are unsure.

You now have a defensible shortlist instead of a browser tab full of maybe-maybes.

### Third run — deep dives

> For the top [N] roles, research each company: what they do, recent news, funding or
> headcount trend, tech stack from their careers page, and the likely interview loop.
> One page each, saved as `companies/<company>.md`.

This is where Cowork earns its keep — it's dozens of pages of reading you'd otherwise skim.

---

## Phase 3 — The tracker

Have Claude build the tracker so the formulas are live and you can keep adding rows yourself.

> Create `tracker.csv` with columns: Company, Role, Link, Score, Stage, Applied date,
> Last contact, Next step, Notes. Add conditional formatting for overdue Next steps.

| Stage | Meaning |
| --- | --- |
| `Researched` | Scored, not yet decided |
| `Shortlisted` | You approved it |
| `Drafting` | Application in progress |
| `Submitted` | Done |
| `Follow-up due` | Waiting on them |
| `Closed` | Rejected or withdrawn |

Keep the file in **Drive** rather than a local folder if you want it on every device. Cowork
sessions follow your account, but local files need the desktop app open.

---

## Phase 4 — Applications

This is where judgement matters. Work one at a time, not in bulk.

> Draft an application for [company] using my voice from instructions.md. Reference
> `companies/<company>.md`. Save to `applications/<company>.md` and show me a summary of
> which requirements you addressed and which you deliberately left out. Do not submit.

Then you edit. Then, only if you want:

> Fill the application form at [link] using the contents of `applications/<company>.md`.
> Stop before the final submit button and show me a screenshot.

**Never let it submit unattended.** An unreviewed application with a fabricated claim is a
much worse outcome than a slow search.

### Scheduling the follow-ups

> Every weekday at 09:00, check `tracker.csv` for rows where Stage is `Submitted` or
> `Follow-up due` and the follow-up date has passed. Draft a short follow-up for each and
> put them in `applications/followups/` for my review. Do not send anything.

---

## What to automate vs. what to keep

| Automate | Keep human |
| --- | --- |
| Finding and scoring listings | Deciding what you actually want |
| Company research | The final yes/no on any application |
| Drafting text | Every factual claim about yourself |
| Tracker upkeep | Anything submitted in your name |
| Follow-up reminders | Replying to recruiter questions |

---

## Failure modes to watch

| Symptom | Cause | Fix |
| --- | --- | --- |
| Claude excludes roles you want | Hard filters too strict | Loosen filters, re-run scoring on the full set |
| Applications sound generic | Voice not specified well | Add real sentences to `instructions.md` |
| It submits without asking | Insufficient guardrail | State "do not submit" explicitly, every time |
| Browser task stalls | Site needs login or CAPTCHA | Take over manually, then continue in the same session |
| Vague progress reports | Task too broad for one run | Split into smaller runs with a file output each |
| Tracker drifts out of date | Multiple sessions editing | Make the tracker the single source of truth |

---

## The single most useful instruction

Put this at the top of `instructions.md`:

> Tell me what you excluded and why, not only what you included.

It converts the run from something you have to audit into something you can spot-check in
thirty seconds — which is the difference between automation you trust and automation you
babysit.