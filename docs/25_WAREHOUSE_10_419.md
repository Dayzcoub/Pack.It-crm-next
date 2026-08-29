# 25 Shortages 10.419

Decision: the mandatory withdrawal comment rule also applies to system-triggered withdrawal caused by loss of `shortages.propose_resolution`.

Behavior:
- when an active proposal is automatically withdrawn because its author loses `shortages.propose_resolution`, the system records a standard withdrawal comment automatically;
- the comment states the actual reason for withdrawal, namely that the author no longer has permission to propose shortage resolutions;
- no manual comment is required from the author or warehouse user for this system-triggered withdrawal;
- the proposal remains in shortage history as a withdrawn proposal with the system as initiator, according to decision 10.418;
- the author notification defined in decision 10.415 may use the same underlying reason, but notification delivery and domain history remain separate concerns.

Architecture binding:
- `shortages` owns the withdrawal transition, system initiator, and persisted withdrawal comment;
- `notifications` may deliver the corresponding author notification only after the withdrawal succeeds;
- `audit` records the permission-driven automatic withdrawal independently;
- the system comment satisfies the mandatory withdrawal-comment invariant established in decision 10.388.

MVP:
- every system withdrawal caused by permission loss has a persisted, human-readable standard comment;
- the proposal history clearly distinguishes the system as initiator even though the lifecycle classification remains ordinary withdrawal.
