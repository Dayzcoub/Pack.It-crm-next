# 25 Warehouse — Shortage Close Permission Note

## 10.249. Who can close shortage entries

Decision: shortage entries can be closed by the assigned warehouse keeper, admin/director, and the responsible person assigned by the warehouse keeper.

Rules:
- assigned warehouse keeper can close shortage entry;
- admin/director can close shortage entry;
- responsible person assigned by warehouse keeper can close shortage entry;
- closure must include resolution/result;
- closure is logged with user and time;
- shortage remains open until one of allowed users closes it.

Resolution options:
- missing quantity found;
- quantity corrected after review;
- formal removal/write-off process completed;
- other approved resolution.

Purpose:
- allow delegated follow-up work;
- keep warehouse keeper in control of assignment;
- avoid blocking resolution when responsible person completes the investigation.

MVP approach:
- shortage has optional assigned responsible user;
- close permission: warehouse keeper, assigned responsible, admin/director;
- store closure result and actor.
