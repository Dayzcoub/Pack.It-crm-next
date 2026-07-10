# PACK.IT CRM Next — project guide for AI coding sessions

## What this is

PACK.IT is a full operating platform for a rental and event-production company.

It is not only a 3D constructor, quote calculator, warehouse app or CRM screen set. It is the system where the company plans, sells, assembles, communicates, executes, tracks, documents and closes projects.

The central entity is **Project / Quote** — everything hangs off it: sections, optional 3D scene, BOM, inventory/reservations, warehouse movements, documents, tasks, team, communication, status/history and CRM.

Formula:

```text
Workspace / Company
  -> Project / Quote
  -> Sections / Scene / BOM
  -> Inventory / Reservations / Warehouse movements
  -> Documents / Tech Pack / Client Preview
  -> Team / Tasks / Communication / Field workflow
  -> Status / History / Audit / CRM
```

The 3D constructor is a major entry point and competitive feature, but it must be connected to the same live project data as warehouse, quote, tasks and documents.

## Current status

- **Docs-first / early-stage.** Do not assume a framework, database, hosting model or package manager until the stack is confirmed by docs or explicit instruction.
- The old app (FegCalc / QucCalc) is a **donor of proven logic, formulas, business rules and reference data only** — not a codebase to copy. Brand is PACK.IT / ПАК.ИТ.

## Read before coding a domain

Specs live in `docs/NN_*.md` and newer `docs/**` notes. Read the relevant docs before implementing a domain — the specs are detailed and authoritative.

Also read the matching project skills in `.claude/skills/*/SKILL.md`:

- `.claude/skills/packit-operating-system/SKILL.md` — product scope, cross-domain operating model, positioning.
- `.claude/skills/packit-project-model/SKILL.md` — Project/Quote, sections, statuses, versions, generated outputs.
- `.claude/skills/packit-warehouse/SKILL.md` — catalog, inventory, reservations, deficits, subrent, scanning, movements.
- `.claude/skills/packit-scene-and-techpack/SKILL.md` — SceneModel, 3D constructor, Asset Library, WYSIWYG-like tech pack, client preview.
- `.claude/skills/packit-ui-mobile/SKILL.md` — desktop vs mobile workflows, role-specific UI, field-first mobile surfaces.
- `.claude/skills/packit-comms-and-field/SKILL.md` — project chats, notifications, tasks, checklists, field workflow, intercom roadmap.
- `.claude/skills/packit-security-and-permissions/SKILL.md` — auth, roles, tenant scoping, PII/pricing visibility, audit.
- `.claude/skills/packit-dev-discipline/SKILL.md` — modular architecture, donor-app discipline, dependency/code hygiene.

## Architecture principle (non-negotiable)

Modular, **not a monolith**. Intended shape (`docs/01_SYSTEM_ARCHITECTURE.md` §6):

```text
packages/
  core-*   (project, sections, scene, stage, truss, led, bom, inventory,
            documents, admin, auth, sync, communication) — business logic, no UI
  ui-*     (shell, projects, scene-editor, inventory, admin, mobile-field) — interfaces
  shared-ui, shared-types
```

Calculations, business logic, UI, warehouse and documents stay **separated**.

The donor app accreted god-modules and CSS hacks. Do not repeat that here. Keep modules single-responsibility; prefer deleting/reusing over adding.

## Security is first-class here

This CRM has real **auth/roles/permissions, guest access, temp/permanent keys, action log, future MFA**, plus **client PII, pricing, warehouse and staff data**. Authorization and PII handling are design concerns from day one:

- enforce authz at the data/service layer, not just the UI;
- never trust client-side role checks;
- log privileged and commercially sensitive actions;
- keep secrets server-side;
- only publish intended public/anon keys to client code;
- separate internal discussion from client-visible comments.

## External references captured in docs

- Golova-like reference: rental CRM/ERP and warehouse operations.
- WYSIWYG-like reference: professional working drawings / tech pack output.
- Stage Lab-like reference: fast visual scene assembly / asset library value.
- Axys Vision-like reference: immersive client preview before execution.

PACK.IT should not copy any one of them. It should connect these worlds into one live operating platform.

## Toolkit available on this machine

- **graphify** (`/graphify .`) — map the codebase as a dependency graph once code exists; use it to catch coupling/god-modules early.
- **ponytail** (`/ponytail`, `/ponytail-review`, `/ponytail-audit`) — enforce minimal code; audit for over-engineering. Reach for stdlib/native before deps.
- **ui-ux-pro-max** — design-system / UI guidance for the `ui-*` packages.
- **Anthropic-Cybersecurity-Skills** at `~/Anthropic-Cybersecurity-Skills/` — reference library (MITRE/NIST/D3FEND-mapped) for authz patterns, PII protection, log threat-hunting. Grep it for the relevant `skills/*/SKILL.md` when working on auth, permissions, or handling customer data.

## Conventions

- Docs and project skills are the source of truth; if code and docs disagree, flag it.
- Commit style: linear history on `main`; `gh` is authenticated for this repo.
- Do not create stack/framework scaffolding until the stack decision is documented.
