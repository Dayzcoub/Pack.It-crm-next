# PACK.IT CRM Next — coding agent instructions

These instructions apply to Codex, Claude Code and any other coding agent working in this repository.

## Product intent

PACK.IT is a full operating platform for rental and technical event-production companies.

It must connect:

- Project / Quote;
- sections and technical calculators;
- optional 3D SceneModel;
- BOM;
- warehouse inventory, reservations and movements;
- documents and tech packs;
- team, tasks, communication and field workflows;
- permissions, history and audit.

Do not treat PACK.IT as only a 3D constructor, only a CRM, only a quote calculator, or only a warehouse app.

## Read first

Before coding a domain, read the relevant docs and skills:

- `CLAUDE.md` — project guide and domain skill index.
- `.claude/skills/packit-operating-system/SKILL.md` — product scope and operating model.
- `.claude/skills/packit-project-model/SKILL.md` — Project/Quote, sections, statuses, outputs.
- `.claude/skills/packit-warehouse/SKILL.md` — warehouse, reservations, deficits, subrent, scanning.
- `.claude/skills/packit-scene-and-techpack/SKILL.md` — SceneModel, 3D, asset library, tech pack, client preview.
- `.claude/skills/packit-ui-mobile/SKILL.md` — desktop/mobile and role-specific UX.
- `.claude/skills/packit-comms-and-field/SKILL.md` — communication, tasks, field work, intercom roadmap.
- `.claude/skills/packit-security-and-permissions/SKILL.md` — auth, roles, PII, pricing, tenant separation, audit.
- `.claude/skills/packit-dev-discipline/SKILL.md` — modularity, donor-app rules, dependency discipline.
- Relevant `docs/**` notes for the exact domain.

Docs and skills are the source of truth. If code and docs disagree, stop and flag it.

## Ponytail development discipline

All coding agents must follow Ponytail-style development rules.

Before writing new code, apply this ladder:

1. Is this change actually required? If not, do not implement it.
2. Does the codebase already have this? Reuse it.
3. Can the standard library or language feature do it? Use that.
4. Can the platform/native API do it? Use that.
5. Is an existing dependency already available? Use it instead of adding another one.
6. Can the same behavior be implemented with less code and less abstraction? Do that.
7. Only then add the smallest new code that solves the task.

Do not remove or skip:

- security boundaries;
- authorization checks;
- input validation at trust boundaries;
- error handling for operational workflows;
- accessibility basics;
- explicit user-requested behavior;
- tests for business-critical domain rules.

Ponytail does **not** mean careless code. It means minimal, direct, maintainable code.

## Architecture rules

When code begins, keep domains separated:

```text
packages/
  core-project
  core-sections
  core-scene
  core-stage
  core-truss
  core-led
  core-bom
  core-inventory
  core-documents
  core-admin
  core-auth
  core-sync
  core-communication
  ui-shell
  ui-projects
  ui-scene-editor
  ui-inventory
  ui-admin
  ui-mobile-field
  shared-ui
  shared-types
```

Exact names may change, but the separation must remain.

Rules:

- Domain logic goes into core packages, not UI components.
- UI components render and orchestrate; they do not own pricing, warehouse or permission truth.
- Generated PDFs, tech packs, warehouse lists and client previews must be projections of the same ProjectModel / SceneModel data.
- Do not create separate manual truth for drawings, quote, BOM, warehouse and tasks.
- Do not create god modules that mix stage, truss, LED, pricing, BOM, warehouse and UI.
- Do not start with framework scaffolding until the stack decision is documented.

## Donor app rule

Old FegCalc / QucCalc code is donor knowledge only:

- formulas;
- business rules;
- accepted behavior;
- reference data;
- UI lessons and edge cases.

Do not blindly copy its code structure, CSS habits or god modules.

## Dependency discipline

Before adding a dependency, explain why the platform, standard library and existing dependencies are insufficient.

Prefer:

- small pure functions;
- explicit domain types;
- direct data transformations;
- tests around business rules;
- fewer abstractions until there are multiple real use cases.

Avoid:

- dependency-first implementation;
- speculative plugin systems;
- abstractions with one implementation;
- config objects that mix unrelated domains;
- CSS hacks and `!important` arms races;
- UI-only state as business truth.

## Security and permissions

PACK.IT handles client PII, pricing, warehouse state, staff data and operational history.

Requirements:

- enforce permissions at data/service/API level, not only UI;
- keep tenant/workspace separation explicit;
- keep secrets out of repo and client bundles;
- separate internal comments from client-visible comments;
- log privileged and commercially sensitive actions;
- never expose internal prices, margins, warehouse data or staff-private data to client previews unless explicitly intended.

## Testing expectations

When code exists, prioritize tests for:

- quote/project status transitions;
- BOM generation;
- warehouse availability by project dates;
- reservation conflicts;
- deficit and subrent behavior;
- permission boundaries;
- document generation from source data;
- scene-to-BOM traceability;
- mobile field workflow state changes.

Do not rely only on component snapshots for business-critical logic.

## Agent behavior

For each implementation task, briefly identify:

- which domain docs/skills were read;
- source of truth data model;
- smallest viable change;
- tests or checks run;
- any intentional Ponytail shortcut marked with `ponytail:`.

If using Claude Code with Ponytail plugin installed, use `/ponytail` for implementation, `/ponytail-review` for over-engineering review of diffs, and `/ponytail-audit` for whole-repo bloat audits.

If using Codex or another agent without Ponytail plugin access, apply the Ponytail ladder manually using this file as the shared instruction source.
