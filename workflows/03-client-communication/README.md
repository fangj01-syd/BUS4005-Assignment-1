# 03 · Client communication — inbox, return letters and fee reminders

> Sample portfolio for BUS4005 Assessment 1. Harbourside Accounting and all figures are invented. Use the structure, not the content.

## What this workflow covers

Everything the practice writes to clients after onboarding: sorting incoming email, explaining the finished return, and chasing unpaid fees.

**Triggers:** an email arrives; a return is finalised; an invoice becomes overdue. **Owners:** front desk, accountant, accounts officer.

## Prompts in this workflow

| ID | Prompt | Runs when | Human checkpoint | Automation / Risk | Evaluation |
|---|---|---|---|---|---|
| [P06](../../prompts/P06.md) | Client email triage | Every email to the shared inbox | Staff member it is routed to; the AI never replies | Very High / Medium | [P06](../../evaluations/P06.md) |
| [P07](../../prompts/P07.md) | Plain-English return summary letter | Return finalised | Accountant edits and signs; never sent without approval | Medium / High | [P07](../../evaluations/P07.md) |
| [P08](../../prompts/P08.md) | Overdue fee reminder | 14, 30 and 60 days overdue | Accounts officer sends; partner approves anything over 60 days | High / Medium | [P08](../../evaluations/P08.md) |

## Prompt chain

```
Shared inbox ─► P06 Triage ─► front desk / accountant / partner
Finalised return ─► P07 Client letter ─► accountant signs
Accounting software (overdue invoices) ─► P08 Fee reminder
```

## Why this workflow

150+ emails a day in peak season, with urgent ATO letters buried among routine questions; clients who do not understand their return call back; and about 1 in 8 invoices is paid late.
