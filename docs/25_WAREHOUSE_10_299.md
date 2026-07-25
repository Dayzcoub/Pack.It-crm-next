# 25 Shortages 10.299

Decision: if the confirmed value is greater than the assigned user's proposed value, treat it as a separate final action rather than acceptance with adjustment.

Architecture binding:
- reduced confirmation within the same result type uses `shortages.accept_proposal`;
- a greater confirmed value uses a separate `shortages.resolve` use case;
- downstream changes are coordinated through public module boundaries and their own permissions.

Example:
- assigned user proposes `found: 2`;
- an authorized resolver confirms `found: 3`;
- this is not acceptance with adjustment;
- it is recorded as a separate final shortage action.

MVP:
- acceptance with adjustment may only reduce the proposed value within the same result type;
- increasing the proposed value creates a normal separate action;
- the original proposal remains visible in shortage domain history;
- no proposal-acceptance notification is produced for the increased value;
- the separate action requires `shortages.resolve` within the applicable scope;
- no role name bypasses application authorization.