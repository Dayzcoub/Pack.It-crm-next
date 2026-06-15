# 25 Warehouse — Write-Off Rejection Note

## 10.221. Rejected write-off request behavior

Decision: if admin/director rejects a write-off request, the item remains in lost status. The rejection must include a required explanation.

Rules:
- rejection does not automatically move the item to another status;
- item remains in lost status after rejection;
- admin/director must provide a rejection reason/comment;
- the requester should be able to see the rejection reason;
- rejection action must be logged with user, date, time, item, request, and reason.

Purpose:
- keep status changes deliberate;
- make rejection accountable and understandable;
- avoid silent changes from the approval workflow.

MVP approach:
- require rejection reason field;
- keep item in lost status;
- allow a separate manual/status workflow later if the item is found, repaired, or reclassified.
