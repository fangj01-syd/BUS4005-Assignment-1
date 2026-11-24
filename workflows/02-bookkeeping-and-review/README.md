# 02 · Bookkeeping and review — from bank feed to a checked return

> Sample portfolio for BUS4005 Assessment 1. Harbourside Accounting and all figures are invented. Use the structure, not the content.

## What this workflow covers

Bookkeeping for business clients and the quality check before a return is lodged. The AI suggests and flags; the bookkeeper and the registered tax agent decide.

**Trigger:** monthly bank feed import. **Ends when:** the accountant completes the final review. **Owners:** bookkeeper, accountant.

## Prompts in this workflow

| ID | Prompt | Runs when | Human checkpoint | Automation / Risk | Evaluation |
|---|---|---|---|---|---|
| [P04](../../prompts/P04.md) | Bank transaction coding | Bank feed imported | Bookkeeper bulk-accepts high-confidence codes only; codes the rest | High / High | [P04](../../evaluations/P04.md) |
| [P05](../../prompts/P05.md) | Reconciliation exception summary | After month-end reconciliation | Bookkeeper checks before the client call | Medium / Medium | [P05](../../evaluations/P05.md) |
| [P10](../../prompts/P10.md) | Pre-lodgement consistency check | Before the accountant's final review | Accountant reviews every flag; the AI never approves a return | Medium / High | [P10](../../evaluations/P10.md) |

## Prompt chain

```
Bank feed ─► P04 Transaction coding ─► P05 Exception summary ─┐
Document tracker (P03, workflow 01) ───────────────────────────┼─► P10 Pre-lodgement check ─► accountant review
```

## Why this workflow

About 15,000 transactions a month across 120 clients are coded one by one, and the most common review finding is a document received but left out of the return. Both are high-volume, rule-based checks where the AI can do the first pass.
