# Sprint Delivery Triage Policy

- Version: 2.1
- Status: **CURRENT — this is the only version in effect**
- Effective since: 2026-10-15
- Supersedes: version 1.3, kept at `docs/policies/archive/triage_policy_v1.3.md` for audit only

## 1. Scope

This policy governs every task delivery that lands on a sprint integration
branch of the `SprintHubBoard` repository. A sprint integration branch is a
branch whose name matches `dev/<developer-login>`. Any branch that does not
match this pattern — for example `spike/*` experiment branches, or archived
cycle branches — is out of scope and must be ignored completely.

This policy applies only to deliveries graded from its effective date
onwards. Rows that already exist in the registry were recorded under earlier
policy versions. They are historical records: leave every one of them exactly
as it is. Do not re-grade, re-label, or otherwise edit existing rows while
applying this policy, even where an old row looks inconsistent with the
current cut-offs.

## 2. Triage score

Every delivered task directory contains a `task_meta.json` file with a
`triage_score` field: a decimal number between 0 and 10, reported to exactly
two decimal places (for example `7.25`). Read `triage_score` from that file.
Do not recompute it, round it, or infer it from any other field.

## 3. Priority tiers

| Priority tier   | Condition                          |
|-----------------|-------------------------------------|
| `P1-FastTrack`  | `triage_score >= 7.25`               |
| `P2-Standard`   | `4.50 <= triage_score < 7.25`       |
| `P3-Backlog`    | `triage_score < 4.50`               |

Cut-offs are inclusive on the lower bound: a score of exactly `7.25` is
`P1-FastTrack`, and a score of exactly `4.50` is `P2-Standard`. There are
exactly three tiers. Never merge two tiers into one, never rename a tier,
and reproduce tier labels verbatim, hyphen and capitalization included.

## 4. Legacy-migration cap

If `task_meta.json` sets `risk_flag` to the exact value `legacy-migration`,
the task can never be graded above `P2-Standard`, no matter how high its
triage score is. This is the only exclusion in this policy. Any other
`risk_flag` value — for example `experimental`, or no value at all — has no
effect on grading.

## 5. Implementation status

A delivered task counts as `implemented` only if its directory contains BOTH
of the following files, each present and non-empty:

- `docs/task.md`
- `evaluation/main.py`

No other file is required or checked. If either file is missing or empty, the
task is `implementing`. The wording is exactly `implemented` or `implementing`.

## 6. Registry update

For every delivered task found on a `dev/*` integration branch, add exactly
one new row to the task registry database on the Notion page `Task Tracker`,
with these columns:

- `Task Name` — the delivered task directory name
- `Task Status` — `implemented` or `implementing`, per section 5
- `Implementor` — the developer whose integration branch carries the
  delivery (the `implementor` field of `task_meta.json`)
- `Triage Score` — per section 2, written as a number
- `Priority` — per sections 3 and 4

Existing registry rows must be left untouched (see section 1).

## 7. Prime pool

Create a branch named `primepool` based on `main`. Copy the full task
directories — file names and file contents unchanged — of exactly those new
deliveries that are BOTH:

1. graded `P1-FastTrack` under sections 3 and 4, and
2. `implemented` under section 5

into `tasks/primepool/<task-directory-name>/` on the `primepool` branch.
Tasks that are `P2-Standard`, `P3-Backlog`, or `implementing` must not be
copied, and out-of-scope branches contribute nothing to the pool.
