# 25 Warehouse — Process Rules Manual Change History Note

## 10.120. Manual process rules change history

Decision: manual edits of warehouse process rules should be logged.

Store:
- user;
- date and time;
- process key;
- rule key;
- old value;
- new value;
- event type.

Rules:
- visible to admin/director in warehouse settings or audit area;
- not shown in daily warehouse operation screens;
- keep it lightweight for MVP;
- no full settings versioning is required at the start.

MVP:
- save a small diff for each manual rule edit;
- keep process rules editable after each edit;
- use the history for admin clarity, not for daily operator workflow.
