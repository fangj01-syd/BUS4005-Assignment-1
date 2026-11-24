# 01 · Onboarding — from booking to a complete set of documents

> Sample portfolio for BUS4005 Assessment 1. Harbourside Accounting and all figures are invented. Use the structure, not the content.

## What this workflow covers

A client books a tax return online. The practice has to tell them what to bring, chase anything missing, and file every document they upload, so the accountant starts the appointment with a complete set of documents.

**Trigger:** online booking. **Ends when:** the document tracker shows nothing missing. **Owner:** client services officer.

## Prompts in this workflow

| ID | Prompt | Runs when | Human checkpoint | Automation / Risk | Evaluation |
|---|---|---|---|---|---|
| [P01](../../prompts/P01.md) | Welcome email and document checklist | Client books | Officer checks and sends the same day | High / Medium | [P01](../../evaluations/P01.md) |
| [P02](../../prompts/P02.md) | Missing-document reminder | 7, 14 and 21 days after P01 if items are missing | Reminders 1–2 send automatically with an audit log; officer checks reminder 3 | Very High / Medium | [P02](../../evaluations/P02.md) |
| [P03](../../prompts/P03.md) | Document intake classifier | Every upload | Low-confidence files go to a person | High / Medium | [P03](../../evaluations/P03.md) |

## Prompt chain

```
Booking ─► P01 Welcome + checklist
                     │
Client uploads ─► P03 Intake classifier ─► document tracker ─► P02 Reminders (only items still missing)
                                                     └──────► P10 Pre-lodgement check (workflow 02)
```

## Why this workflow

About 900 clients a season. Incomplete documents are the main reason appointments are rescheduled, and each one wastes about 45 minutes of an accountant's time.
