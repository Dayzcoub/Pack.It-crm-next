# 25 Warehouse — Shortage Write-off Rejection Note

## 10.252. Rejected write-off returns shortage to open state

Decision: if admin/director rejects a write-off request related to a shortage, the shortage entry returns to open state with rejection reason saved.

Rules:
- rejected write-off does not close shortage;
- shortage returns to open/current list;
- rejection reason is required;
- rejection reason is visible in shortage detail/history;
- assigned warehouse keeper and responsible person should see rejection result;
- shortage remains available for further investigation or reassignment.

Purpose:
- avoid losing unresolved shortage after rejected write-off;
- keep clear explanation of why write-off was rejected;
- allow continued follow-up.

MVP approach:
- admin/director rejects approval request;
- system saves rejection reason;
- linked shortage status becomes open;
- notification/update goes to warehouse keeper summary.
