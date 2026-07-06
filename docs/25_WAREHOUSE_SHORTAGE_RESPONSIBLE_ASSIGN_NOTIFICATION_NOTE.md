# 25 Warehouse — Shortage Responsible Assign Notification Note

## 10.275. Notification to assigned shortage responsible

Decision: when a user is assigned as responsible for a shortage, the system should send them a notification.

Rules:
- notification is sent after responsible person is assigned or changed;
- assigned user receives notification regardless of their role;
- notification should include source project, missing item/row, missing quantity, and current status;
- notification opens the shortage detail card;
- assignment event is logged in shortage action history;
- if responsible person is changed, the new responsible person receives notification.

Purpose:
- make sure the assigned person knows they are responsible for follow-up;
- reduce lost/unhandled shortages;
- keep ownership clear.

MVP approach:
- on assign/change responsible action, create notification for assigned user;
- notification leads to shortage detail card;
- store assignment event with actor and timestamp.
