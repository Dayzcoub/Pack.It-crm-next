# 25 Warehouse — Transfer Status Permission Note

## 10.148. Who can update transfer statuses

Decision: transfer statuses may be updated by the assigned responsible person or by the project manager.

Rules:
- the assigned responsible person can mark the transfer as departed;
- the assigned responsible person can mark the transfer as delivered;
- the project manager can also update these statuses;
- other project participants should not update transfer statuses by default;
- admin/director may still have override access through general administrative permissions if needed.

Statuses covered:
- departed;
- delivered.

Purpose:
- keep responsibility clear;
- avoid random status changes by unrelated users;
- let the project manager control the transfer if the responsible person cannot update the status.

MVP approach:
- allow status updates for responsible user and project manager;
- store who changed the status and when;
- keep wider permission tuning for later if needed.
