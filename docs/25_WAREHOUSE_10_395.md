# 25 Shortages 10.395

Decision: forcibly releasing another user's edit lock does not automatically transfer that lock to the administrator who released it.

Behavior:
- the forced-release action only clears the current exclusive edit lock;
- after the release, the proposal becomes unlocked and available according to the normal lock-acquisition rules;
- if the administrator wants to edit the proposal, they must explicitly open it for editing and acquire a new lock through the standard flow;
- the previous editor's form is handled according to decisions 10.392 and 10.394;
- the forced-release reason and audit record remain attached to the administrative action from decision 10.393.

Architecture binding:
- lock ownership and lock release are transient coordination concerns and do not change the shortage's business resolution by themselves;
- forced release requires the administrative permission established by decision 10.393;
- audit records the forced-release action separately from any later edit or resolution action.

MVP:
- forced release leaves the proposal unlocked;
- no implicit lock handoff occurs;
- any subsequent editor, including the administrator, must acquire a fresh lock normally.
