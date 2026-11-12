# SprintHubBoard

Delivery repository for the current sprint cycle.

Branch layout:

- `main` — policy documents and the repository baseline.
- `dev/<developer-login>` — per-developer sprint integration branches. Every
  task delivered this sprint lives in `tasks/<task-name>/` on one of these
  branches.
- `spike/*` — experiments and prototypes. Not part of the sprint scope.
- archived cycle branches (for example `dev-archive-2025`) — previous cycle
  leftovers. Not part of the sprint scope.

The only policy version in effect is
`docs/policies/triage_policy_v2.1.md`. Versions under
`docs/policies/archive/` are superseded and kept for audit only.

The sprint registry lives in the task registry database on the Notion page
`Task Tracker`.
