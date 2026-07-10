# PACK.IT Security, Roles and Permissions Skill

Use this skill before implementing auth, users, roles, guests, invitations, API access, tenant separation, secrets, PII, pricing visibility, audit logs, or permission-sensitive UI.

## Main rule

PACK.IT stores client data, project data, prices, warehouse data, staff data and operational history. Security and authorization are product architecture, not UI decoration.

## Security principles

- Enforce permissions at data/service/API level, not only in UI.
- Treat tenant/workspace separation as mandatory from the start.
- Never trust client-side role checks.
- Keep secrets server-side.
- Use publishable/anon client keys only when intended by the chosen stack.
- Log privileged and commercially sensitive actions.
- Do not commit `.env`, private keys, tokens or secrets.

## Role families

Expected role families:

- Owner/Admin;
- Manager;
- Technical Director;
- Warehouse;
- Technician;
- Sound/Light/Screen/Truss/Stage specialists;
- Driver/Loader;
- Accountant/Finance;
- Viewer;
- Guest/Client;
- Invited specialist.

Exact permissions should be modeled as capabilities/policies, not hardcoded role names everywhere.

## Permission examples

Control access to:

- project list;
- client PII;
- financial data and margins;
- quote editing and sending;
- warehouse stock and reservations;
- deficit/subrent decisions;
- admin settings;
- user/role management;
- tech pack visibility;
- client preview visibility;
- task assignment;
- status transitions;
- audit log access.

## Guest/client access

Client or guest access should be deliberately scoped:

- selected project preview;
- selected quote/documents;
- approval actions;
- client-visible comments only;
- no internal warehouse, margin, internal chat, staff private data unless explicitly allowed.

Temporary/permanent links or keys must have:

- scope;
- expiration where relevant;
- revocation;
- audit trail;
- creator/owner.

## Audit log candidates

Log at least:

- quote sent/approved/changed;
- project status change;
- permission/role changes;
- user invitations;
- warehouse movements;
- reservations and shortages;
- subrent decisions;
- document generation/sending;
- client approval;
- destructive actions.

## Implementation guidance

Before coding a sensitive feature:

1. Identify data sensitivity.
2. Identify roles/capabilities.
3. Define backend/data-layer enforcement.
4. Define UI visibility separately.
5. Define audit events.
6. Define tenant/workspace scoping.
7. Add tests for unauthorized access.

## Red flags

- `if (user.role === 'admin')` scattered everywhere.
- Hidden buttons without backend enforcement.
- Public links with no revocation or scope.
- Client preview exposing warehouse/internal prices.
- Missing audit for quote, permission or warehouse changes.
- Secrets in repo, logs, screenshots or client bundle.
