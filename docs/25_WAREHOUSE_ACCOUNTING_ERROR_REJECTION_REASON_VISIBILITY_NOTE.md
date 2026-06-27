# 25 Warehouse — Accounting Error Rejection Reason Visibility Note

## 10.263. Rejection reason visibility for accounting error correction

Decision: when accounting error correction is rejected, the notification shows only the rejection fact. The rejection reason is shown inside the shortage detail card.

Rules:
- notification/card preview should stay compact;
- notification shows that correction was rejected;
- rejection reason is not shown directly in notification preview;
- rejection reason is available in the shortage detail card;
- assigned warehouse keeper and responsible person can open the detail card to view the reason;
- rejection reason remains stored in history.

Purpose:
- keep notifications short and clean;
- avoid overloading notification cards;
- preserve full context inside the shortage detail view.

MVP approach:
- notification text: correction rejected;
- link/open action leads to shortage detail;
- detail view shows rejection reason, actor, timestamp, and current open status.
