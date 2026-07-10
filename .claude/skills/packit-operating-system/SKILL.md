# PACK.IT Operating System Skill

Use this skill before changing product strategy, architecture, module boundaries, or any cross-domain workflow.

## Product definition

PACK.IT is a full operating platform for rental and technical event-production companies.

It is not only:

- a 3D constructor;
- a quote calculator;
- a warehouse app;
- a CRM;
- a chat app.

It is the connected system where the company plans, sells, assembles, communicates, executes, tracks, documents and closes projects.

## Core operating model

```text
Workspace / Company
  -> Clients / Contacts / Venues
  -> Projects / Quotes / Documents / Finance
  -> Catalog / Assets / Warehouse / Inventory / Reservations
  -> Scene / 3D constructor / BOM / Tech Pack
  -> Team / Tasks / Calendar / Transport / Services
  -> Project communication / Notifications / Field workflows
  -> Reports / Analytics / History / Audit log
```

## Non-negotiables

- Project/Quote is the main business container.
- The system must connect visual construction, BOM, warehouse, quote, tasks, team and documents.
- Avoid isolated calculators that cannot feed the real project data model.
- Avoid UI-only role checks; authorization must be enforceable at data/service level.
- All operational facts should have history/audit where relevant: quote changes, stock movements, assignments, approvals, status changes.
- Multi-company / tenant separation must be considered from the beginning.

## Positioning

Use this internal positioning:

```text
PACK.IT = operating system for technical event production.
3D Scene = one powerful project entry point.
Warehouse/CRM/Tasks/Comms = equally first-class operational modules.
```

External inspiration map:

- Golova-like: rental CRM/ERP and warehouse operations.
- WYSIWYG-like: professional technical drawing output.
- Stage Lab-like: fast visual scene assembly / asset library value.
- Axys Vision-like: immersive client preview before execution.

PACK.IT must not copy any one of these. It must connect them into one live workflow.

## Implementation guidance

When implementing or editing anything:

1. Identify which ProjectModel / WorkspaceModel data it reads and writes.
2. Decide whether it affects warehouse, quote, tasks, documents, communication, or audit.
3. Keep domain logic in core packages, not inside UI components.
4. Keep UI views as projections of the same live data, not separate manual documents.
5. If a change creates duplicated truth, stop and redesign.

## Red flags

- A PDF generated from data different from the quote.
- A client render that does not match the warehouse/BOM.
- A task list that is manually disconnected from the project sections.
- A warehouse reservation that is not tied to project dates.
- A role-based screen hide without backend/data-layer enforcement.
- A module that requires copy-paste instead of structured transfer between domains.
