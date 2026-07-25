# 25 Shortages 10.385

Decision: the responsible person may withdraw their proposal before a final shortage resolution is recorded.

Behavior:
- withdrawal is available only while the proposal remains pending and the shortage has not received a final result;
- the withdrawn proposal is no longer available for acceptance;
- the shortage remains open and continues to require a final resolution;
- the withdrawn proposal remains visible in the shortage history with the status `Отозвано`;
- withdrawal does not delete or rewrite the original proposal data;
- after withdrawal, the responsible person may submit a new proposal if they still have `shortages.propose_resolution` permission.

Architecture binding:
- proposal withdrawal is a named `shortages` use case and is authorized independently from role names;
- `shortages` owns the proposal state transition and shortage history entry;
- withdrawal creates no inventory, reservation, subrent, or warehouse-operation side effect;
- any notification is dispatched only after the withdrawal transaction succeeds;
- `audit` separately records the significant action.

MVP:
- pending proposal can be withdrawn before final resolution;
- withdrawn proposal cannot be accepted;
- shortage stays open;
- original proposal remains traceable in history.
