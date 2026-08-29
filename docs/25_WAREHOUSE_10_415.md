# 25 Shortages 10.415

Decision: when an active proposal is automatically closed because its author loses `shortages.propose_resolution`, the author must receive a separate notification explaining why the proposal was closed.

Behavior:
- losing `shortages.propose_resolution` closes the author's active proposals according to decision 10.413;
- each affected proposal remains preserved in shortage/proposal history;
- after the successful automatic closure, the proposal author receives a notification;
- the notification states that the proposal was closed because the author no longer has permission to propose shortage resolutions;
- the notification must not imply that the proposal was rejected on its merits or that the shortage itself was resolved;
- restoring the permission later does not restore the closed proposal, according to decision 10.414.

Architecture binding:
- `shortages` owns the proposal state transition and its history;
- `notifications` delivers the author notification only after the source transition succeeds;
- `audit` independently records the relevant permission-driven closure and associated significant actions where required by the system audit policy;
- role names do not grant this behavior by themselves: the canonical permission is `shortages.propose_resolution`.

MVP:
- permission loss closes affected active proposals;
- the author receives a separate notification with the closure reason;
- the proposal remains available in history as closed and is not automatically restored later.
