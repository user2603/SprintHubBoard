# Sprint Delivery Triage Policy

- Version: 1.3
- Status: **DEPRECATED — superseded by version 2.1 since 2026-10-15.
  DO NOT USE FOR GRADING.** Kept for audit of the 2025 delivery cycle only.

## 1. Scope

(2025 wording) This policy governs task deliveries merged to the integration
branches of the 2025 delivery cycle.

## 2. Priority tiers

| Priority tier   | Condition                          |
|-----------------|-------------------------------------|
| `P1-FastTrack`  | `triage_score >= 8.00`               |
| `P2-Standard`   | `5.00 <= triage_score < 8.00`       |
| `P3-Backlog`    | `triage_score < 5.00`               |

## 3. Implementation status (2025 rule)

A delivered task counts as `implemented` only if its directory contains ALL
THREE of the following files, each present and non-empty:

- `docs/task.md`
- `evaluation/main.py`
- `task_config.json`

If any of the three is missing or empty, the task is `implementing`.

## 4. Registry update

(2025 wording) Rows were graded under the cut-offs of section 2 of this
version. Registry rows recorded under this version are historical records
once version 2.1 takes effect.

## 5. Prime pool (2025 rule)

The 2025 pool collected deliveries graded `P1-FastTrack` under section 2 of
this version and `implemented` under section 3 of this version.
