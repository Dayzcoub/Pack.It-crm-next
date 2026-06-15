# 25 Warehouse — Item Status Base and Extensible Note

## 10.205. Warehouse item status base set

Decision: use a base MVP status set for warehouse items, but keep the status model extensible.

Base MVP statuses:
- available — item is available;
- reserved — item is reserved for a project;
- picked — item is picked / prepared for handout;
- out — item is handed out / on project;
- returned — item has returned;
- in_repair — item is in repair;
- quarantine — item is blocked / under review;
- written_off — item is written off;
- lost — item is lost.

Rules:
- the base set is enough for MVP;
- do not hard-code the model so it cannot be extended;
- allow future admin/director configuration of additional statuses;
- custom statuses should still map to availability logic where needed;
- status changes must be logged with user, date, time, and source context.

Purpose:
- keep MVP simple;
- avoid blocking future company-specific warehouse workflows;
- support both small teams and stricter warehouse processes later.

MVP approach:
- implement the base statuses first;
- design the data model so new statuses can be added later;
- keep important availability-impacting statuses clearly mapped.
