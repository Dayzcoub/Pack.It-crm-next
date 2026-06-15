# 25 Warehouse — Transfer Departed Notification Note

## 10.149. Notification when transfer has departed

Decision: when transfer equipment is marked as departed, the receiving project should be notified.

Rules:
- the notification is sent when the transfer status changes to departed;
- the receiving project team should see that the equipment is already on the way;
- the notification should reference the equipment, source project/site, target project/site, and responsible person;
- the notification should not create a separate document;
- the transfer block remains visible in both related picking lists.

Example:
- RCF kit is marked as departed from project A;
- project B receives a notification that the RCF kit has left the first site and is on the way.

Purpose:
- reduce uncertainty for the receiving team;
- help the second site prepare for arrival;
- make project-to-project equipment movement visible without adding extra paperwork.

MVP approach:
- send notification to the target project manager and relevant assigned team members;
- store notification time and status change history;
- show current transfer status in the transfer block.
