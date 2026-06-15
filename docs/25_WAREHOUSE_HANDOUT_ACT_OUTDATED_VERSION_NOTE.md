# 25 Warehouse — Handout Act Outdated Version Note

## 10.165. Outdated versions of generated handout acts

Decision: if a new handout act is generated after changes, previous generated acts should remain in history and be marked as outdated.

Rules:
- do not delete or overwrite previous generated acts;
- each generated act remains in document history;
- the latest generated act is treated as current;
- previous versions are marked as outdated;
- outdated versions should still be available for audit/history when permissions allow.

Purpose:
- keep document history transparent;
- make it clear which act version is current;
- avoid confusion when a handout act is regenerated after changes.

MVP approach:
- store a version/status field for generated handout acts;
- possible statuses: current, outdated;
- when a new version is generated, older versions for the same handout become outdated;
- keep the handout act internal.
