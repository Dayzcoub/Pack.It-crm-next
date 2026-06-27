# 25 Warehouse — Accounting Error Rejection Note

## 10.262. Rejected accounting error correction returns shortage to open state

Decision: if admin/director rejects accounting error correction for a shortage, the shortage entry returns to open state with rejection reason saved.

Rules:
- rejected accounting error correction does not close shortage;
- shortage returns to the open/current list;
- rejection reason is required;
- rejection reason is visible in shortage detail/history;
- assigned warehouse keeper and responsible person should see rejection result;
- shortage remains available for further investigation, reassignment, found quantity, write-off request, or another correction proposal.

Purpose:
- avoid losing unresolved shortage after rejected correction;
- keep clear explanation of why correction was rejected;
- allow continued follow-up.

MVP approach:
- admin/director rejects correction approval request;
- system saves rejection reason;
- linked shortage status becomes open;
- notification/update goes to warehouse keeper summary.
