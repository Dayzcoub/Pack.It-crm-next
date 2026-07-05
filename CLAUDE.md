# PACK.IT CRM Next — project guide for AI coding sessions

## What this is
Project/estimate **CRM** for a rental & event-production company. The central
entity is **Project / Quote** — everything (sections, optional 3D scene, BOM,
inventory/reservations, documents, status/history) hangs off it. The 3D
constructor is an **optional module**, not the product.

Formula: `Project/Quote → Sections → (optional) 3D Scene → BOM → Inventory/Reservations → Documents → Status/History/CRM`.

## Current status
- **Docs-only.** No code yet. **No stack chosen** — the docs describe the domain,
  not the technology. Do NOT assume Next.js/DB/etc. until the stack is confirmed.
- The old app (FegCalc / QucCalc) is a **donor of proven logic, formulas, business
  rules and reference data only** — not a codebase to copy. Brand is PACK.IT / ПАК.ИТ.

## Read before coding a domain
Specs live in `docs/NN_*.md` (Project/Quote, Sections, BOM, Inventory/Warehouse,
Documents, Admin/Roles, Auth, Calendar, Transport, Team, Services, …). Read the
relevant `docs/` note before implementing that domain — the specs are detailed
and authoritative.

## Architecture principle (non-negotiable)
Modular, **not a monolith**. Intended shape (`docs/01_SYSTEM_ARCHITECTURE.md` §6):
```
packages/
  core-*   (project, sections, scene, stage, truss, led, bom, inventory,
            documents, admin, auth, sync)  — business logic, no UI
  ui-*     (shell, projects, scene-editor, inventory, admin)  — interfaces
  shared-ui, shared-types
```
Calculations, business logic, UI, warehouse and documents stay **separated**.
The donor app accreted god-modules (a 1560-line config mixing stage+truss+BOM)
and a ~6600-`!important` CSS arms race — do not repeat that here. Keep modules
single-responsibility; prefer deleting/reusing over adding (see ponytail below).

## Security is first-class here (unlike the donor static PWA)
This CRM has real **auth/roles/permissions, guest access, temp/permanent keys,
action log, future MFA**, plus **client PII and pricing**. Authorization and PII
handling are design concerns from day one, not afterthoughts:
- enforce authz at the data layer (row/tenant scoping), not just the UI;
- never trust client-side role checks; log privileged actions;
- keep secrets server-side; only publishable/anon keys in client code.

## Toolkit available on this machine
- **graphify** (`/graphify .`) — map the codebase as a dependency graph once code
  exists; use it to catch coupling/god-modules early.
- **ponytail** (`/ponytail`, `/ponytail-review`, `/ponytail-audit`) — enforce
  minimal code; audit for over-engineering. Reach for stdlib/native before deps.
- **ui-ux-pro-max** — design-system / UI guidance for the `ui-*` packages.
- **Anthropic-Cybersecurity-Skills** at `~/Anthropic-Cybersecurity-Skills/` —
  reference library (MITRE/NIST/D3FEND-mapped) for authz patterns, PII protection,
  log threat-hunting. Grep it for the relevant `skills/*/SKILL.md` when working on
  auth, permissions, or handling customer data.

## Conventions
- Docs are the source of truth; if code and a `docs/` note disagree, flag it.
- Commit style: linear history on `main`; `gh` is authenticated for this repo.
