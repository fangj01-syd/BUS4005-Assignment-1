# 📚 Prompt Library — Tax-Season Client Services (Small Accounting Practice)

> **Assessment 1 | BUS4005 Artificial Intelligence for Business — SAMPLE**  
> Prepared by: Jacky Fang (teaching sample, not a student submission) | Business field: Accounting practice — tax-season client services  
> Model tested on: Claude Opus 5.5 (Anthropic)  
> Last updated: 22 November 2026

> **Please do not copy this business or these prompts.** Harbourside Accounting (a six-person practice in Parramatta, NSW) and every figure here are invented. Use the structure, not the content. This README follows the unit's Markdown prompt-library template.

---

## What This Library Does

This prompt library supports workflow automation in **tax-season client services at a small Australian accounting practice**, from a client booking an appointment to the return being approved and the fee paid. It contains **10 documented, tested and iterated prompts**, organised by the stage of the workflow they support.

**Scope boundary:** no prompt gives tax advice or decides a tax treatment. A registered tax agent makes every technical decision.

Each prompt entry follows the same structure:
- The exact prompt text (with placeholders)
- The workflow task it supports
- The problem it solves
- Its automation potential
- Known risks and mitigations
- Version history and test results

---

## 📂 Folder Structure

```
BUS4005-Assignment-1/
│
├── README.md          ← You are here (library index)
│
├── prompts/           ← one file per prompt (P01–P10), all six sections above
│   ├── P01.md  …  P10.md
│
└── tests/             ← evaluation evidence: criteria, every input, actual output, pass/fail
    ├── P01.md  …  P10.md
```

> 💡 The unit template groups prompts into one folder per workflow (e.g. `01-onboarding/`). This sample keeps one `prompts/` folder and shows the workflow stage in the table below instead. Either layout is fine — what matters is that every prompt has the same sections and its test evidence is easy to find.

---

## 📊 Library Summary Table

| ID | Prompt Name | Workflow | Automation Level | Risk Level | Status |
|----|-------------|----------|-----------------|------------|--------|
| [P01](prompts/P01.md) | Welcome email and document checklist | Onboarding | High | Medium | ✅ Tested (v1.2) |
| [P02](prompts/P02.md) | Missing-document reminder | Onboarding | Very High | Medium | ✅ Tested (v1.2) |
| [P03](prompts/P03.md) | Document intake classifier | Onboarding | High | Medium | ✅ Tested (v1.3) |
| [P04](prompts/P04.md) | Bank transaction coding | Bookkeeping | High | High | ✅ Tested (v1.2) |
| [P05](prompts/P05.md) | Reconciliation exception summary | Bookkeeping | Medium | Medium | ✅ Tested (v1.2) |
| [P06](prompts/P06.md) | Client email triage | Client communication | Very High | Medium | ✅ Tested (v1.2) |
| [P07](prompts/P07.md) | Plain-English return summary letter | Client communication | Medium | High | ✅ Tested (v1.2) |
| [P08](prompts/P08.md) | Overdue fee reminder | Accounts receivable | High | Medium | ✅ Tested (v1.3) |
| [P09](prompts/P09.md) | Weekly workload report for the partner | Practice management | High | Low | ⚠️ Tested – 1 fail (v1.1) |
| [P10](prompts/P10.md) | Pre-lodgement consistency check | Quality control | Medium | High | ✅ Tested (v1.1) |

**Automation levels:** Very High / High / Medium / Low  
**Risk levels:** High (always needs human review) / Medium (spot-check recommended) / Low (can automate with audit)  
**Tested** = current version run on invented inputs with Claude Opus 5.5 on 22 November 2026; full results in `tests/`. P09 failed one check — kept on purpose, with the fix noted.

---

## 🔗 Prompt Chaining Map

Several prompts are designed to work in sequence. The chains below show how the output of one prompt feeds the next.

```
ONBOARDING CHAIN
P01 (Welcome + checklist) → P02 (Missing-document reminders) ◄── tracker ── P03 (Intake classifier)

BOOKKEEPING → QUALITY CONTROL CHAIN
P04 (Transaction coding) → P05 (Exception summary) → P10 (Pre-lodgement check) → accountant review
P03 (Intake classifier) ─────────────────────────────┘

CLIENT COMMUNICATION
P06 (Email triage) → routes to front desk / accountant / partner
Finalised return → P07 (Client letter)

STAND-ALONE
P08 (Fee reminders) · P09 (Weekly workload report)
```

---

## ⚙️ Prompting Strategies Used

| Strategy | Prompts | Why chosen |
|----------|---------|------------|
| Role + task + context (RACE-style structure) | All | Consistent structure, so versions can be compared fairly |
| Grounding constraint ("Use ONLY…") | P01, P02, P04, P05, P07, P09 | Stops the model inventing figures, codes or checklist items |
| Fixed category list | P03, P06 | Predictable labels the tracker and inbox rules can act on |
| JSON output format | P03, P04, P06 | Machine-readable for the job tracker and email routing |
| Uncertainty rules ("NOT FOUND", confidence, "unknown") | P03, P04, P05 | Tells the model what to do when information is missing instead of guessing |
| Explicit exclusions ("Do not…") | P01, P04, P06, P07, P08, P09, P10 | Keeps tax advice, GST decisions and legal threats out of the output |
| Word/format limits | P01, P02, P05, P07, P08, P09 | Output is ready to use without heavy editing |
| Business rule inside the prompt | P02, P06, P08 | Tone by reminder number, routing rules, 60-day payment-plan offer |
| Two-step self-check | P10 | Model re-checks each flag and removes any it cannot point to |

---

## 📝 Iteration Evidence

Every prompt file has a full version-history table. **Commit history = version log**: each commit message says what changed and why.

| Prompt | Versions | Key improvement |
|--------|----------|-----------------|
| P01 | v1.0 → v1.2 | Added exclusions (no tax advice, no refund estimate, no TFN by email) after a draft estimated a refund |
| P03 | v1.0 → v1.3 | JSON output, then "NOT FOUND" + confidence after the model guessed a financial year |
| P04 | v1.0 → v1.2 | Chart-of-accounts grounding, then a private/business rule and "do not decide GST" |
| P08 | v1.0 → v1.3 | Length and tone limits, then the 60-day payment-plan rule |
| P10 | v1.0 → v1.1 | Step-2 self-check added; 4 of 4 planted gaps found, no false flags |

> Earlier versions in each file are illustrative: they show how a version log should read. Only the current version of each prompt was run in testing.

**Next versions suggested by the real tests:** P01 output "NEEDS REVIEW: reason" when data is missing · P03 record a financial year only if stated · P08 add a [CONTACT_DETAILS] placeholder · P09 define "in progress" as any status except lodged.

---

## 💡 Tips for Your Own Library

1. Create the repo (or OneDrive folder) on day one and save your first, weak prompt as v1.0 — it is evidence, not a mistake.
2. Change **one thing at a time** and record what changed and why.
3. Write your pass criteria **before** you run the test, and keep the failures.
4. Keep the outputs. They show why each version changed.
5. Before you submit, open the link in a private browser window to check the marker can see it.

---

## 📖 References

- Anthropic (2025). *Prompt engineering overview.* Claude Docs.
- Kartaca (2026). *Standardizing enterprise intelligence with a corporate prompt library.*
- MIT Sloan (2025). *Prompt engineering is so 2024 — try these prompt templates instead.*
- Microsoft (2025). *Get started with prompt library — Copilot Studio.*
- VE3 Global (2025). *10 key elements of a prompt library for enterprise tasks.*

---
*Tested on Claude Opus 5.5 (Anthropic), 22 November 2026, with invented data. Prepared by Jacky Fang for BUS4005, La Trobe University Sydney.*
