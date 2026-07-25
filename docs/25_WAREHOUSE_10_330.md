# 25 Shortages 10.330

Decision: if reconciliation after an uncertain submission shows that the shortage has already been changed by another action and the original resolution is no longer applicable, the form closes and the user is shown the current shortage state.

Behavior:
- the client reloads the shortage from the server after an uncertain submission result;
- if the intended action is already reflected in the current shortage state, the normal successful-completion flow applies;
- if another action changed the shortage and the submitted resolution can no longer be applied, the current form is not reused or silently adapted;
- the form closes;
- the shortage view refreshes to the latest server-confirmed state;
- the user is informed that their attempted action was not applied because the shortage changed before completion;
- no automatic repeat submission is performed;
- any new action must be started against the refreshed shortage state.

Architecture binding:
- `shortages` remains the source of truth for the current shortage state and its domain history;
- reconciliation is a read operation performed after an ambiguous transport result and does not itself create a domain or audit event;
- applicability of `shortages.resolve` is determined by server-side state and concurrency checks, not by the client form snapshot;
- the client in `apps/web` closes the stale form and refreshes its read model when the server state no longer matches the action context;
- notifications and audit records are created only for actions that were actually committed successfully.

MVP:
- an outdated form cannot overwrite or reinterpret a shortage changed by another action;
- the latest shortage state is displayed after reconciliation;
- the user receives a clear explanation that their action was not applied;
- the user must start a new action from the refreshed state;
- no duplicate resolution, notification, or audit event is created.
