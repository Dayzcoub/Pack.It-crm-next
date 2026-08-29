# 25 Warehouse 10.438

Decision: moving an equipment unit to `Blocked` requires at least a short mandatory reason/comment explaining why the unit is unavailable.

Behavior:
- `Ready -> Blocked` is an explicit warehouse-domain operation;
- the operation cannot be committed without a non-empty reason/comment;
- the reason is stored in operation/history data together with actor and timestamp;
- the reason explains operational unavailability but does not create a separate maintenance workflow by itself;
- `Blocked` equipment remains part of `on_hand` but is excluded from `available`;
- restoring `Blocked -> Ready` is a separate operation and does not rewrite the original blocking record;
- if a later maintenance/incident module is introduced, it may reference the blocking operation rather than replacing warehouse history.

Architecture binding:
- equipment availability/state remains owned by `inventory`;
- the state transition is recorded using the common `WarehouseOperation` envelope from 10.433;
- applied state transitions are immutable under the general correction rule from 10.432;
- PostgreSQL remains the source of truth;
- `audit` independently records significant actions without replacing warehouse operation history.

MVP:
- blocking a unit always requires a short reason/comment;
- no structured damage taxonomy is required for MVP;
- one free-text reason is enough to keep the workflow simple and understandable;
- the original reason remains preserved in history even after the unit later returns to `Ready` or is written off.
