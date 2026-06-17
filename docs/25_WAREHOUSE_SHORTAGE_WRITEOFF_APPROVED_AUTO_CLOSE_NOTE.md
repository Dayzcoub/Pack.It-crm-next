# 25 Warehouse — Shortage Write-off Approved Auto Close Note

## 10.253. Approved write-off auto-closes shortage

Decision: if admin/director approves write-off related to a shortage, the shortage entry is closed automatically with a confirmation step.

Rules:
- approval action must show final confirmation before applying result;
- after confirmation, shortage is automatically closed;
- closure result is stored as write-off / formal removal;
- closure actor is the approving admin/director;
- closure timestamp is stored;
- linked stock adjustment/write-off action is logged;
- warehouse keeper summary is updated after closure.

Purpose:
- avoid extra manual closure after admin/director already approved final action;
- keep final write-off controlled by confirmation;
- preserve clear audit trail.

MVP approach:
- admin/director opens approval request;
- system shows confirmation dialog;
- on confirm, system applies write-off and closes linked shortage entry automatically.
