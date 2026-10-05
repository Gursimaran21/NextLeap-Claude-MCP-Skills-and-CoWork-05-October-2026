---
name: prd-writer
description: Writes a Product Requirements Document in the user's own house style, learned from examples they supply. This skill should be used when the user asks to "write a PRD", "draft a PRD", "create a product requirements document", "turn these notes into a PRD", "spec this out", or shares rough notes, meeting transcripts, or screenshots and asks for a formal spec.
license: MIT
metadata:
  author: Gursimaran
  version: 1.0.0
  category: product
  tags:
    - product-management
    - writing
    - templates
---

# PRD Writer

Produce a PRD that matches the user's established format, voice, and level of detail — not a generic template.

## Core principle

A PRD is a **communication artefact**, not a form. The value is in matching what the reader already expects. Infer structure, heading names, ordering, tone, and depth from the examples provided, and reproduce them.

When no examples exist, ask for one before drafting. A single real PRD from the user is worth more than any amount of inference.

## Workflow

### Step 1 — Acquire the raw material

Accept whatever the user provides: messy notes, a meeting transcript, a Slack thread, a brainstorm, screenshots, a voice summary, or a competitor's spec.

Do not require it to be organised. Messy input is the normal case.

### Step 2 — Resolve the house style

Determine the target format, in this order of preference:

1. **Examples supplied in this conversation** — use them directly.
2. **A reference PRD in `references/house-style.md`** — use the documented structure.
3. **Neither available** — ask which of the structures in `references/house-style.md` to follow, or ask the user to paste an example.

Record the resolved choice before drafting. Do not silently mix two styles.

### Step 3 — Extract the substance

Pull out, or ask for, whichever of these the material does not already contain:

- Problem statement and who experiences it
- Target user and the job they are hiring the product to do
- Success metrics, with target values
- Scope — explicit in-scope and out-of-scope lists
- Requirements, split into must-have / should-have / nice-to-have
- Constraints — timeline, team, budget, technical, regulatory
- Open questions and dependencies

Never invent a metric, a date, or a target number. If one is needed and absent, insert a clearly marked placeholder such as `[TBD — needs target]`.

### Step 4 — Draft

Follow the resolved structure exactly. Match:

- **Heading names and casing** — if their PRD uses `## Goals` rather than `## Objectives`, use `## Goals`.
- **Ordering** — follow their section sequence, not a conventional one.
- **Depth per section** — if their problem statement is one paragraph, do not write four.
- **Voice** — first person plural, third person, or imperative; match what they use.

Where the structure calls for a section the material does not support, write `## Not covered` with a one-line reason rather than padding it with speculation.

### Step 5 — Self-check before returning

Verify each of the following:

- [ ] Section order and headings match the resolved style
- [ ] No invented facts, numbers, dates, or stakeholders
- [ ] Every placeholder is visibly marked `[TBD]`
- [ ] Out-of-scope section exists and is non-empty
- [ ] Success metrics are measurable, not adjectives
- [ ] The document stands alone — no unexplained references to the conversation

Report the resolved style back to the user in one line so they can correct it cheaply if it is wrong.

## Common failure modes

| Failure | Correction |
| --- | --- |
| Applying a generic template over the user's format | Stop. Re-read Step 2 and match their structure literally. |
| Fabricating targets to fill a table | Use `[TBD]` and list them for the user to fill. |
| Padding thin sections to look complete | Write `## Not covered` instead. |
| Mixing two reference structures | Pick one, state which, and stay consistent. |
| Rewriting the user's voice into corporate prose | Match register. Plain beats polished. |

## Reference

Read `references/house-style.md` for the documented fallback structures, a section-by-section
checklist, and a worked excerpt showing the expected level of detail.