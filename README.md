# BUS4005 Assessment 1 — Sample prompt library portfolio

This is the **sample portfolio** that goes with the annotated sample report for BUS4005 *Artificial Intelligence for Business*, La Trobe University (Sydney).
It shows what a strong portfolio link can look like: every prompt, every version, and the test evidence behind it.

> **Please do not copy this business or these prompts.** Harbourside Accounting (a six-person practice in Parramatta, NSW) and every figure here are invented. Use the structure, not the content.

## The workflow

Tax-season client services, from a client booking an appointment to the return being approved and the fee paid.
**Scope boundary:** no prompt gives tax advice or decides a tax treatment. A registered tax agent makes every technical decision.

```
Booking ─► P01 Welcome + checklist ─► P02 Reminders ◄─ tracker ─ P03 Intake classifier ─┐
Bank feed ─► P04 Transaction coding ─► P05 Exception summary ──────────────────────────┼─► P10 Pre-lodgement check ─► Accountant review
Shared inbox ─► P06 Triage ─► staff        Finalised return ─► P07 Client letter       │
Accounting software ─► P08 Fee reminders    Job tracker ─► P09 Weekly report (logic-tested)
```

## Library summary

| ID | Prompt | Workflow stage | Feeds into | Automation / Risk | Status | Version |
|---|---|---|---|---|---|---|
| [P01](prompts/P01.md) | Welcome email and document checklist | Onboarding 1 | P02 | High / Medium | Tested | v1.2 |
| [P02](prompts/P02.md) | Missing-document reminder | Onboarding 2 | — | Very high / Medium | Tested | v1.2 |
| [P03](prompts/P03.md) | Document intake classifier | Onboarding 3 | P02 (tracker), P10 | High / Medium | Tested | v1.3 |
| [P04](prompts/P04.md) | Bank transaction coding | Bookkeeping 1 | P05 | High / High | Tested | v1.2 |
| [P05](prompts/P05.md) | Reconciliation exception summary | Bookkeeping 2 | P10 | Medium / Medium | Tested | v1.2 |
| [P06](prompts/P06.md) | Client email triage | Communication 1 | Routes to staff | Very high / Medium | Tested | v1.2 |
| [P07](prompts/P07.md) | Plain-English return summary letter | Communication 2 | — | Medium / High | Tested | v1.2 |
| [P08](prompts/P08.md) | Overdue fee reminder | Accounts receivable | — | High / Medium | Tested | v1.3 |
| [P09](prompts/P09.md) | Weekly workload report for the partner | Practice management | — | High / Low | Logic-tested | v1.1 |
| [P10](prompts/P10.md) | Pre-lodgement consistency check | Quality control | Reviewer | Medium / High | Tested | v1.1 |

**Status:** *Tested* = run on sample inputs, results in the file. *Logic-tested* = reviewed against invented data but not run on real records.

## How to read this portfolio

- `prompts/` — one file per prompt, with the same sections: prompt text · workflow / task · problem solved · automation potential · risks & limitations · **version history** · **test evidence**.
- `tests/` — one test set per prompt: what it checks, the test cases (including edge cases), a sample input, and the result. All test inputs are invented; the results show the format, so run and record your own.

## Tips for your own portfolio

1. Create the repo on day one and save your first, weak prompt as v1.0 — it is evidence, not a mistake.
2. Change **one thing at a time** and commit with a message that says what and why, e.g. `P03 v1.2 – added JSON output`.
3. Keep the outputs, especially the failures. They show why each version changed.
4. Label anything you could not test.
5. Before you submit, open the link in a private browser window to check the marker can see it.

---
*Sample portfolio — all data and test results are illustrative. Prepared by Jacky Fang for BUS4005, La Trobe University Sydney.*
