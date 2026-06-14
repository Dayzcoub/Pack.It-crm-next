# 25 Warehouse — Preset Rollback No Time Limit Note

## 10.118. No time limit for preset rollback

Decision: preset rollback should not have a time limit.

Rules:
- rollback is available for the latest preset application only;
- rollback is single-use for that preset application;
- no 24-hour or similar time window is required;
- availability ends after rollback is used or after another preset is saved.

Reason:
- admin may notice that rules are not comfortable later;
- one-step rollback is enough for MVP;
- time-based expiration is unnecessary.

MVP:
- store rollback availability flag;
- store previous rules snapshot for latest preset application;
- clear availability after rollback or after next preset save.
