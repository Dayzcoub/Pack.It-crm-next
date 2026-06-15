# 25 Warehouse — Custom Status Availability Mapping Note

## 10.207. Custom status availability impact

Decision: every custom warehouse status must define how it affects item availability.

Availability impact options:
- available for booking;
- unavailable;
- conditionally available / requires confirmation.

Rules:
- custom status cannot be created without availability impact mapping;
- admin/director defines this mapping when creating or editing a custom status;
- availability logic and reservation checks must use this mapping;
- conditionally available statuses should require explicit confirmation in booking/reservation workflow;
- status changes must be logged with user, date, time, and source context.

Purpose:
- prevent custom statuses from breaking booking and reservation logic;
- allow company-specific status names while preserving predictable availability behavior;
- support future workflow expansion without losing stock control.

MVP approach:
- base statuses have fixed availability behavior;
- custom statuses require an availability impact field;
- only admin/director can configure custom statuses and their availability impact.
