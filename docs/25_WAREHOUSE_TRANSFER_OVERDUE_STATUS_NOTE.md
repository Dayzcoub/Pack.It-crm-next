# 25 Warehouse — Transfer Overdue Status Note

## 10.151. Transfer overdue / alert status

Decision: if transfer equipment has not departed or has not been delivered by the planned time, the system should show an overdue / alert status.

Rules:
- planned departure time may be tracked;
- planned delivery time may be tracked;
- if the transfer is still planned after the planned departure time, show an alert;
- if the transfer is not delivered after the planned delivery time, show an alert;
- alert status is for control and visibility, not an automatic cancellation.

Purpose:
- keep project-to-project equipment movement under control;
- help the manager notice a delay early;
- make transfer risks visible to the receiving project team;
- avoid losing important equipment movement between two project schedules.

MVP approach:
- show overdue / alert status in the transfer block;
- notify the project manager when a transfer becomes overdue;
- keep the responsible person visible;
- store the planned times and actual status update times;
- do not automatically cancel or reassign the transfer.
