# 25 Warehouse — Custom Status Permission Note

## 10.206. Who can add custom warehouse statuses

Decision: only company admin or director can add and configure custom warehouse statuses.

Rules:
- ordinary warehouse users, technicians, managers, and technical directors do not add custom statuses by default;
- custom status creation and configuration is limited to admin/director permissions;
- status usage by other roles can still depend on normal warehouse workflow permissions;
- every custom status change should be logged.

Purpose:
- keep warehouse status logic controlled;
- prevent status chaos in daily operations;
- allow company-level customization without losing consistency.

MVP approach:
- implement base statuses first;
- allow admin/director-only customization later;
- keep custom statuses mapped to availability logic where needed.
