# 25 Warehouse 10.298

Decision: acceptance with adjustment is allowed only when the final result keeps the same result type as the assigned user's proposal.

Example:
- assigned user proposes `found`;
- warehouse keeper selects `write off`;
- this is not acceptance with adjustment;
- it is recorded as a separate final action with a different result type.

MVP:
- acceptance with adjustment may change values or details only within the same result type;
- changing the result type creates a normal separate action;
- the original proposal remains visible in history;
- no proposal-acceptance notification is sent when the final action uses a different result type;
- the final action is performed by warehouse keeper, admin, or director and is logged normally.
