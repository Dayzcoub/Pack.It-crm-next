# 25 Warehouse — Write-Off Request Notification Note

## 10.220. Write-off request notifications and approval list

Decision: a write-off request must both notify admin/director and appear in a separate approval list.

Rules:
- when a warehouse user creates a write-off request, admin/director receives a notification;
- the request is also added to a dedicated list such as pending approvals;
- notification is not the only tracking mechanism;
- approval list should show item, requester, reason/comment, date/time, and current status;
- admin/director can confirm or reject the request from the approval flow;
- all actions must be logged.

Purpose:
- make urgent requests visible immediately;
- keep a persistent queue for review;
- avoid losing requests in notifications.

MVP approach:
- create notification for admin/director;
- add request to pending approvals list;
- final confirmation remains admin/director-only.
