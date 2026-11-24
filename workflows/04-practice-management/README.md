# 04 · Practice management — the partner's weekly view

> Sample portfolio for BUS4005 Assessment 1. Harbourside Accounting and all figures are invented. Use the structure, not the content.

## What this workflow covers

A weekly summary for the managing partner of where work is stuck, built only from the job tracker export.

**Trigger:** Friday tracker export. **Ends when:** the summary is discussed at the Monday meeting. **Owner:** practice manager.

## Prompts in this workflow

| ID | Prompt | Runs when | Human checkpoint | Automation / Risk | Evaluation |
|---|---|---|---|---|---|
| [P09](../../prompts/P09.md) | Weekly workload report for the partner | Every Friday | Practice manager checks the numbers before forwarding | High / Low | [P09](../../evaluations/P09.md) — 1 fail, kept on purpose |

## Prompt chain

```
Job tracker export ─► P09 Weekly report ─► practice manager check ─► partner (Monday meeting)
```

## Why this workflow

The manual report takes about 1.5 hours, so it is skipped in the busiest weeks — exactly when the partner needs it. P09 failed one check in testing ("in progress" was read literally); the fix for the next version is in the prompt file.
