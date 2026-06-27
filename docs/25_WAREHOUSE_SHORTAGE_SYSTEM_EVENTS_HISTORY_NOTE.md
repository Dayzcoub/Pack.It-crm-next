# 25 Warehouse — Shortage System Events History Note

## 10.265. System events in shortage action history

Decision: shortage action history should include both human actions and important system events.

Rules:
- collapsible action history shows user actions;
- collapsible action history also shows important automatic system events;
- examples of system events: automatic quantity restore, automatic shortage close, moved to history, approval request created, notification sent;
- system events should be visually distinguishable from human actions;
- each system event should include timestamp and related result/change;
- human actions still show actor, timestamp, action type, and reason/comment where applicable.

Purpose:
- make the full shortage lifecycle understandable;
- avoid hidden automatic changes;
- support audit and troubleshooting.

MVP approach:
- add event type: user/system;
- show events chronologically in the collapsible history block;
- for system events, show concise label and changed quantity/status where relevant.
