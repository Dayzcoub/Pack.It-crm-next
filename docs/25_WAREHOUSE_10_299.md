# 25 Warehouse 10.299

Decision: if the confirmed value is greater than the assigned user's proposed value, treat it as a separate final action rather than acceptance with adjustment.

Example:
- assigned user proposes `found: 2`;
- warehouse keeper confirms `found: 3`;
- this is not acceptance with adjustment;
- it is recorded as a separate final action.

MVP:
- acceptance with adjustment may only reduce the proposed value within the same result type;
- increasing the proposed value creates a normal separate action;
- the original proposal remains visible in history;
- no proposal-acceptance notification is sent for the increased value;
- the final action is performed by warehouse keeper, admin, or director and is logged normally.
