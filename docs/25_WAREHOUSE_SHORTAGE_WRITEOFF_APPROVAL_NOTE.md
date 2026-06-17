# 25 Warehouse — Shortage Write-off Approval Note

## 10.251. Write-off result requires approval

Decision: if shortage is closed with write-off/formal removal result, the system should start approval request for admin/director.

Rules:
- choosing write-off result does not immediately finalize stock removal;
- approval request is created for admin/director;
- shortage remains linked to the approval request;
- final stock change happens only after approval;
- rejection keeps shortage open or returns it to follow-up state with reason;
- all actions are logged.

Purpose:
- prevent silent write-off from shortage closure;
- keep final stock changes under admin/director control;
- preserve audit trail.

MVP approach:
- close action with write-off result creates pending approval;
- notify admin/director;
- store approval status and link to shortage entry.
