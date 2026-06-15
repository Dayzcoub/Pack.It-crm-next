# 25 Warehouse — Base Status Availability Mapping Note

## 10.208. Base warehouse status availability impact

Decision: define the availability impact for the base MVP warehouse statuses immediately.

Base status availability mapping:
- available — available for booking/reservation;
- reserved — unavailable;
- picked — unavailable;
- out — unavailable;
- returned — conditionally available / requires confirmation before returning to available stock;
- in_repair — unavailable;
- quarantine — unavailable;
- written_off — unavailable;
- lost — unavailable.

Rules:
- booking and reservation logic must use this mapping;
- returned status does not automatically mean available;
- returned items should be checked/confirmed before becoming available again;
- status changes must be logged with user, date, time, and source context.

Purpose:
- keep availability behavior predictable;
- avoid accidentally booking items that are reserved, out, damaged, missing, or not checked yet;
- support clear warehouse lifecycle logic for MVP.

MVP approach:
- implement this mapping for the base status set;
- custom statuses must also define their availability impact separately;
- only admin/director can configure custom statuses and their mappings.
