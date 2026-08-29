# 25 Shortages 10.413

Decision: if the author of an active shortage-resolution proposal loses the `shortages.propose_resolution` permission, that active proposal is automatically closed as no longer valid for consideration.

Behavior:
- the proposal is not left available for acceptance after its author loses the required proposal permission;
- the system closes the proposal automatically rather than waiting for a warehouse user or the former author to act;
- the closed proposal remains in shortage/proposal history;
- the history must show that the proposal was closed because the author no longer had the required permission;
- the shortage itself remains open unless another accepted resolution closes it;
- if a new proposal is still needed, it must be submitted by a user who currently has `shortages.propose_resolution`;
- a warehouse user who already has the proposal open must not be able to accept it after the permission revocation; the action must reconcile against the latest proposal state.

Architecture binding:
- permissions are evaluated independently of role names;
- `shortages` owns the proposal lifecycle transition from active to closed;
- the proposal-acceptance use case must validate the latest proposal state and current applicability in the same transaction boundary;
- a stale acceptance attempt follows the existing conflict/reconciliation rules;
- the automatic closure and its reason are preserved in shortage-domain history;
- `audit` independently records the permission-driven automatic closure as a significant action.

MVP:
- active proposals from users who lose `shortages.propose_resolution` are automatically closed;
- such proposals can no longer be accepted or edited;
- they remain visible in history with the system closure reason;
- the open shortage can receive a new proposal from an authorized user.
