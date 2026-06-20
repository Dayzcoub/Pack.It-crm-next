# 25 Warehouse — Manual Correction Reason Required Note

## 10.259. Manual correction requires reason

Decision: when shortage is closed with manual correction result, a reason/comment is required.

Rules:
- manual correction cannot be completed without a reason;
- system records who made the correction;
- system records when the correction was made;
- reason is shown in shortage history;
- correction must show before/after quantity where applicable.

Purpose:
- make it clear why stock was corrected manually;
- preserve accountability for manual adjustments;
- support audit and later investigation.

MVP approach:
- require correction reason text field;
- save actor, timestamp, source project, previous quantity, corrected quantity, and reason;
- move shortage to closed/history after valid correction.
