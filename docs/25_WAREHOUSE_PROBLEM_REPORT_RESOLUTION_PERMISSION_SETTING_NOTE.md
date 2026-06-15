# 25 Warehouse — Problem Report Resolution Permission Setting Note

## 10.200. Who can close the requires resolution status

Decision: the permission to close the requires resolution status should be configurable by the company admin or director.

Rules:
- do not hard-code one fixed role for closing the status;
- company admin/director can configure who is allowed to close or resolve problem reports;
- possible allowed groups may include managers, warehouse users, technicians, admins, directors, or custom roles;
- the closing action should always be logged with user, date, time, and resolution/action.

Purpose:
- support different company sizes and workflows;
- allow small teams to keep the process flexible;
- allow larger teams to enforce stricter approval.

MVP approach:
- add a company-level setting for who can close requires resolution;
- default can be conservative, but adjustable by admin/director;
- keep the report internal by default.
