# PACK.IT UI and Mobile Workflow Skill

Use this skill before implementing user interface, navigation, role-specific screens, responsive layouts, mobile field workflows, dashboards, constructor UI, or design-system work.

## Main rule

PACK.IT must not be a desktop CRM squeezed onto mobile. Mobile and desktop are different operating contexts.

Desktop is for planning, editing, estimating, managing and reviewing.

Mobile is for field execution, scanning, communication, tasks, checklists, approvals and quick project context.

## Desktop priorities

- project overview;
- quote editing;
- section configuration;
- 2D/3D scene editing;
- warehouse availability matrix;
- documents and PDF generation;
- admin/roles/settings;
- analytics/reports;
- calendar/resource planning.

Desktop UI may show dense information, but must use clear hierarchy and domain grouping.

## Mobile priorities

- today's projects;
- my tasks;
- project chat/notifications;
- scan item;
- loading/return checklist;
- site checklist;
- issue/photo report;
- contact responsible person;
- quick project documents/view-only tech pack;
- approval/confirmation actions.

Mobile should not expose all admin complexity unless the role and context require it.

## Role-specific UI

Different roles should have different primary surfaces:

- Manager: client/project/quote/status.
- Warehouse: scan/pick/load/return/inventory/deficits.
- Technician: tasks/checklists/docs/chat/site issues.
- Technical Director: project tech pack, scene, team, approvals, shortages.
- Admin: users, roles, settings, catalog, audit.
- Client/Guest: preview, quote, approval, selected documents only.

Do not only hide admin panels in UI. Permissions must also exist in data/service logic.

## Design principles

- Compact, readable, professional event-tech UI.
- Use shared design tokens and reusable components.
- Avoid CSS wars and `!important` hacks.
- Separate layout components from domain logic.
- Prefer clear workflow screens over giant all-in-one forms.
- Make incomplete/deficit/problem states visible and actionable.
- Preserve dark/light themes where relevant, but do not duplicate styling logic.

## Mobile constructor caution

3D/scene editing on mobile should be limited and task-specific unless explicitly designed.

Good mobile scene use cases:

- view project;
- inspect zones;
- open object details;
- confirm positions/checklists;
- add issue/photo/comment;
- simple measurement/reference.

Risky mobile use cases:

- full dense 3D editing;
- complex truss/LED construction;
- large tables and multi-step admin forms.

## Output quality

For every UI change, ask:

1. Which role is this for?
2. Is this planning or field execution?
3. What is the next action after reading this screen?
4. Does the UI expose only the data this role should see?
5. Does the UI write to the correct ProjectModel/WorkspaceModel data?

## Red flags

- One universal dashboard for all roles.
- Mobile pages that are just desktop tables scaled down.
- Important operational actions hidden behind tiny controls.
- UI state not backed by domain state.
- Color/status indicators with no action or explanation.
