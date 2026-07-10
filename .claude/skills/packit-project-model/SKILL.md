# PACK.IT Project Model Skill

Use this skill before implementing projects, quotes, sections, BOM, statuses, history, approvals, documents, or cross-module project flows.

## Main rule

Project/Quote is the central operating entity. Everything operational should either belong to a project, derive from it, or clearly belong to workspace-level catalogs/settings.

## Project should connect

```text
Project
  -> client / venue / dates / contacts
  -> quote versions / financial status
  -> sections: stage, truss, LED, sound, light, backline, commutation, transport, team, services
  -> optional SceneModel / 3D layout
  -> generated BOM
  -> inventory reservations / shortages / subrent
  -> documents: quote, tech pack, warehouse sheets, crew sheets
  -> tasks / checklists / responsible people
  -> communication threads / notifications
  -> status history / audit log
```

## Quote and project rules

- Quote versions must be explicit. Never silently overwrite commercial truth.
- Project dates drive warehouse availability and crew/transport planning.
- Sections can be incomplete while drafting, but generated documents must show readiness/deficit states honestly.
- A technical project can exist before a final client quote, and quote versions can evolve.
- Any generated BOM must trace back to section items or scene objects.

## Statuses

Design statuses as operational states, not decorative labels.

Examples:

- draft;
- waiting for data;
- ready for quote;
- quote sent;
- approved;
- warehouse preparation;
- loading;
- on site;
- returned;
- closed;
- cancelled.

Each status change should be auditable when it matters.

## Sections

Sections should be modular, but connected by the project shell:

- Stage;
- Truss;
- LED;
- Sound;
- Light;
- Backline;
- Commutation;
- Transport;
- Team;
- Services;
- Documents;
- Warehouse/BOM;
- Communication.

Do not build one giant config object that mixes all domains.

## Generated outputs

Documents and sheets are projections of project data:

- client quote;
- internal estimate;
- tech pack;
- warehouse pick list;
- loading list;
- return list;
- crew task list;
- field checklist;
- client preview link.

If a generated output needs manual overrides, store overrides explicitly with reason/history.

## Implementation checklist

Before coding a Project/Quote feature:

1. Read relevant `docs/NN_*.md` notes.
2. Identify source of truth fields.
3. Identify derived fields and caches.
4. Decide how quote versions and history behave.
5. Decide how permissions work.
6. Decide how it affects documents and notifications.
7. Add tests for domain rules before polishing UI.
