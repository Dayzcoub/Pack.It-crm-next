# 25 Warehouse — Problem Report Auto Status Update Note

## 10.201. Automatic warehouse status update after resolution

Decision: after the problem resolution is closed, the warehouse item status should be updated automatically according to the selected resolution/action.

Rules:
- closing a problem resolution triggers the corresponding warehouse status update;
- the status change must be logged with user, date, time, source report/problem row, and selected resolution;
- the mapping between resolution/action and warehouse status should be predictable;
- if the action is ambiguous, require user confirmation before changing stock status.

Example mappings:
- write off -> written off / removed from active stock;
- send to repair -> in repair;
- move to quarantine -> quarantined / blocked;
- return to active stock -> available;
- found in warehouse -> available or needs review depending on context;
- replace item -> replaced / requires stock correction.

Purpose:
- avoid double work after a problem is resolved;
- keep document decisions and warehouse stock state synchronized;
- reduce manual mistakes in inventory status management.

MVP approach:
- update warehouse status after closing the resolution;
- use a simple action-to-status mapping;
- log every automatic status change;
- keep the report internal by default.
