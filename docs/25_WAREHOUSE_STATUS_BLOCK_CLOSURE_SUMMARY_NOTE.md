# 25 Warehouse — Status Block Closure Summary Note

## 10.226. Warehouse item status lifecycle summary

Decision: close the warehouse item status block and keep the current lifecycle decisions as the MVP baseline.

Base statuses:
- available;
- reserved;
- picked;
- out;
- returned;
- in_repair;
- quarantine;
- written_off;
- lost.

Availability rules:
- available is available for booking/reservation;
- reserved, picked, out, in_repair, quarantine, written_off, and lost are unavailable;
- returned is conditionally available and requires confirmation/check before returning to available;
- custom statuses are allowed, but only admin/director can create or configure them;
- every custom status must define availability impact: available, unavailable, or conditionally available.

Returned and repair flow:
- returned items can be moved to available by warehouse-change users or admin/director after confirmation;
- if a problem requires repair, available status is blocked;
- in_repair must record repair destination: internal repair, external contractor, or service center;
- repair return date is not required for MVP; repair comment is enough;
- item returning from repair goes to returned/check state first, not directly to available;
- use returned with comment/flag instead of a separate check_required status;
- if inspection is OK, no comment is required;
- if inspection finds a problem, comment is required.

Lost and final accounting flow:
- lost status makes item unavailable for projects immediately but keeps it visible in warehouse records until final action;
- warehouse user can request final action with explanation;
- admin/director confirms the final action;
- request notifies admin/director and appears in a review/approval list;
- rejected request leaves item in lost status and requires admin/director rejection reason;
- warehouse user can request returning the item from lost/problem state if it is found;
- admin/director can return it immediately;
- return request also notifies admin/director and appears in the review list;
- confirmed return goes to returned/check first, then after inspection can return to balance/available workflow.

MVP principle:
- keep status model simple but extensible;
- separate availability logic from display labels;
- all status transitions and approval actions must be logged.
