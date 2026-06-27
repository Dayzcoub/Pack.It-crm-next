# 25 Warehouse — Accounting Error Approved Auto Apply Note

## 10.261. Approved accounting error correction auto-applies and closes shortage

Decision: if admin/director approves accounting error correction for a shortage, the system automatically applies the quantity correction and closes the linked shortage entry.

Rules:
- admin/director approval must include final confirmation before applying correction;
- after approval/confirmation, system applies the accounting correction automatically;
- linked shortage entry is closed automatically with result: accounting error corrected;
- actor, timestamp, reason, previous quantity, corrected quantity, and source project are logged;
- if correction is rejected, shortage remains open with rejection reason;
- warehouse keeper and assigned responsible person should see the result in history/notification.

Purpose:
- avoid extra manual steps after approval;
- keep stock correction under admin/director control;
- preserve clear audit trail for accounting changes.

MVP approach:
- warehouse keeper/responsible proposes correction with required reason;
- admin/director opens approval request;
- on confirmation, system applies correction and closes shortage automatically.
