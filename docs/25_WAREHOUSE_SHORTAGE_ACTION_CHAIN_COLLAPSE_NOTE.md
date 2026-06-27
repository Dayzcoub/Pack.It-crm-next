# 25 Warehouse — Shortage Action Chain Collapse Note

## 10.264. Shortage detail action chain in collapsible section

Decision: shortage detail card should include a collapsible action chain/history block.

Rules:
- main shortage detail remains compact;
- full action chain is available in a collapsible section;
- chain shows who created the shortage;
- chain shows who assigned responsible person;
- chain shows partial found actions;
- chain shows write-off requests and approvals/rejections;
- chain shows accounting error correction requests and approvals/rejections;
- chain shows closure actor, closure result, timestamps, comments/reasons where applicable.

Purpose:
- keep shortage card readable;
- preserve complete audit trail;
- make investigation possible without cluttering daily workflow.

MVP approach:
- add collapsible block: action history;
- order actions chronologically;
- each row shows action type, actor, timestamp, result, and optional reason/comment.
