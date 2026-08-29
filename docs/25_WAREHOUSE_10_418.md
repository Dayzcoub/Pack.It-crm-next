# 25 Shortages 10.418

Decision: an active proposal that is automatically closed because its author lost `shortages.propose_resolution` is classified as a normal proposal withdrawal, with the system recorded as the initiator.

Behavior:
- the proposal uses the same withdrawn lifecycle classification as a voluntary withdrawal;
- the withdrawal is not attributed to the proposal author;
- history records the system as the initiator of the withdrawal;
- the reason remains visible in history: the author lost `shortages.propose_resolution`;
- the proposal remains preserved in shortage history and is not restored automatically if the permission is later returned, according to decision 10.414;
- author notification behavior remains governed by decision 10.415;
- an active warehouse review is interrupted immediately according to decision 10.416, without a separate warehouse notification according to decision 10.417.

Architecture binding:
- `shortages` owns the withdrawal state transition and proposal history;
- permission loss is the domain trigger for the system-initiated withdrawal;
- `notifications` sends the author notification only after the withdrawal succeeds;
- `audit` separately records the permission change and resulting system action where applicable.

MVP:
- no separate proposal lifecycle status is introduced specifically for permission-loss closure;
- UI/history may distinguish voluntary and system-initiated withdrawals through initiator and reason metadata rather than a new status.
