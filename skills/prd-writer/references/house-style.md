# PRD house styles

Two fallback structures. If the user has supplied their own examples, ignore this file entirely
and match their examples.

## Style A — Lean

For small, well-understood changes. One page.

```markdown
# [Feature name]

## Problem
[2–4 sentences. What is broken today, for whom, and what it costs.]

## Proposal
[2–4 sentences. What changes, at a high level. No implementation detail.]

## Scope
**In:** [bullet list]
**Out:** [bullet list]

## Success
- [Metric] — target [value] by [date]

## Open questions
- [Question] — owner [name]
```

## Style B — Full

For new products, cross-team initiatives, or anything needing sign-off.

```markdown
# [Product name] — PRD
Owner: [name] · Status: [Draft / In review / Approved] · Last updated: [YYYY-MM-DD]

## 1. Summary
[One paragraph.]

## 2. Problem
[Problem statement. Evidence. Who hurts, how often, how much.]

## 3. Goals and non-goals
**Goals**
- [Goal]

**Non-goals**
- [Explicitly excluded thing]

## 4. Users
**Primary:** [persona] — [the job they are hiring this to do]
**Secondary:** [persona]

## 5. Requirements
### Must have
- [Requirement]
### Should have
- [Requirement]
### Nice to have
- [Requirement]

## 6. Success metrics
| Metric | Baseline | Target | Measured by |
| --- | --- | --- | --- |
| [Metric] | [value] | [value] | [instrument] |

## 7. Out of scope
- [Thing someone will assume is included but is not]

## 8. Constraints
- **Timeline:** [ ]
- **Team:** [ ]
- **Technical:** [ ]
- **Compliance:** [ ]

## 9. Rollout
[Phases, flags, or staged release.]

## 10. Risks
| Risk | Likelihood | Impact | Mitigation |
| --- | --- | --- | --- |

## 11. Open questions
- [Question] — owner [name] — needed by [date]

## 12. Appendix
[Research, data, prior art.]
```

## Section checklist

For each section, confirm before returning the draft:

- **Problem** — names a specific person and a specific pain. Not "users want efficiency."
- **Goals** — each is an outcome, not a deliverable. "Cut onboarding to under 2 minutes," not "build onboarding v2."
- **Non-goals** — non-empty. The most useful section in the document.
- **Requirements** — testable. If you cannot describe how you would know it works, it is not a requirement.
- **Metrics** — a baseline and a target. A metric without a target is a wish.
- **Out of scope** — phrased so a reader cannot misread it as included.
- **Open questions** — each has an owner and a date. Unowned questions are ignored.

## Worked excerpt

Shows the expected level of detail for Style B, section 2. Note the specificity and the
absence of adjectives where numbers belong.

```markdown
## 2. Problem

Support resolves roughly 340 tickets a week. 61 of those are billing questions that
require a support agent to read the customer's plan tier from the admin panel, then
explain the proration formula in chat.

The formula is correct but undocumented outside two engineer heads. Median resolution
time for these tickets is 11 minutes versus 4 minutes for everything else, and 22% of
them are reopened because the customer did not understand the first answer.

Finance estimates 340 × 11 min ≈ 62 hours a month of agent time spent explaining
arithmetic.
```

### Why this excerpt works

- **Quantified** — volume, time, and cost are all numbers.
- **Attributed** — "Support resolves", "Finance estimates" — not "users".
- **Root cause stated** — the formula is undocumented, which implies the fix.
- **Second-order effect** — the 22% reopen rate is found, not assumed.
- **No filler** — every sentence carries information.