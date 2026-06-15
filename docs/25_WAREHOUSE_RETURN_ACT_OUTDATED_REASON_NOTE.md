# 25 Warehouse — Return Act Outdated Reason Note

## 10.179. Outdated reason for return act versions

Decision: the return act should use the same outdated reason approach as the handout act.

Rules:
- when a new return act version is generated, previous versions are marked as outdated;
- outdated versions should show a reason where available;
- the system may suggest the reason from detected changes;
- the user may edit or replace the suggested reason manually;
- the final reason is stored in document history.

Examples of reasons:
- returned items changed;
- problem rows changed;
- delivery person changed;
- accepted-by user corrected;
- attachments added or changed;
- document regenerated after return correction.

Purpose:
- make return act history understandable;
- avoid unclear outdated document versions;
- reuse the same document logic as handout acts.

MVP approach:
- support auto-suggested reason where possible;
- support manual correction;
- show the final reason in return act history.
