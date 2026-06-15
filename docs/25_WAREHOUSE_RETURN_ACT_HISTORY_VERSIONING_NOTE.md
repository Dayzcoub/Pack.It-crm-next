# 25 Warehouse — Return Act History Versioning Note

## 10.178. Return act history and versions

Decision: the return act should use the same history and versioning approach as the handout act.

Rules:
- each generated return act is stored in document history;
- repeated generation creates a new version;
- the previous version stays available in history;
- the latest version is marked as current;
- older versions are marked as outdated;
- outdated versions may show a reason where available.

Purpose:
- keep return documents auditable;
- avoid overwriting previously generated documents;
- make it clear which return act version is current.

MVP approach:
- store generated return act records with version number or current/outdated status;
- store who generated the act and when;
- keep PDF/file reference if generated;
- reuse the handout act history pattern where possible.
