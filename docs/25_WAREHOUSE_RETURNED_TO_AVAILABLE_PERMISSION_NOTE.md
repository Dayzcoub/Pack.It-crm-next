# 25 Warehouse — Returned to Available Permission Note

## 10.209. Who can confirm returned item availability

Decision: both warehouse-change users and admin/director can confirm moving an item from returned back to available.

Rules:
- returned status is conditionally available and requires confirmation before becoming available;
- users with warehouse change permissions can confirm the item back to available;
- admin/director can also confirm this transition;
- the confirmation must be logged with user, date, time, item, and source context;
- if the returned item has related problems, the system should warn or block according to future problem rules.

Purpose:
- allow normal warehouse staff to restore returned equipment to active stock after checking it;
- keep admin/director override available;
- avoid bottlenecks while preserving auditability.

MVP approach:
- allow returned -> available transition for warehouse-change users and admin/director;
- require explicit confirmation;
- log the transition.
