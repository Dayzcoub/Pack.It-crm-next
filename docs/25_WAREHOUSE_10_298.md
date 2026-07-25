# 25 Shortages 10.298

Decision: acceptance with adjustment is allowed only when the final result keeps the same result type as the assigned user's proposal.

Architecture binding:
- proposal acceptance is an application use case of `shortages` and requires `shortages.accept_proposal`;
- changing the result type is a separate `shortages` resolution use case and requires `shortages.resolve`;
- any required inventory, subrent, or warehouse operation is invoked through that context's public boundary and permissions.

Example:
- assigned user proposes `found`;
- an authorized confirmer selects `write_off`;
- this is not acceptance with adjustment;
- it is recorded as a separate final action with a different result type.

MVP:
- acceptance with adjustment may change values or details only within the same result type;
- changing the result type creates a normal separate shortage action;
- the original proposal remains visible in shortage domain history;
- no proposal-acceptance notification is produced when the final action uses a different result type;
- a `write_off` result must coordinate with `warehouse-operations` instead of mutating inventory directly;
- no role name bypasses application authorization.