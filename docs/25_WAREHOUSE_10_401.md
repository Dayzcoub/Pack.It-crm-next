# 25 Shortages 10.401

Decision: when a remaining shortage quantity becomes smaller than the quantity in another active proposal, that proposal cannot be accepted as-is; its author must adjust it to the current remainder before acceptance.

Behavior:
- partial shortage resolution may reduce the currently open quantity;
- active proposals remain available according to decision 10.400 when they can still apply to the remaining shortage;
- if an active proposal quantity is greater than the current open shortage quantity, the proposal is considered stale for acceptance;
- the warehouse user cannot accept that proposal until its author adjusts the quantity to a value that does not exceed the current remainder;
- the system does not silently clamp or automatically rewrite the proposal quantity during acceptance;
- the author edits the existing active proposal rather than creating an implicit adjusted acceptance on the warehouse side;
- after the proposal is corrected, normal review and acceptance rules apply.

Architecture binding:
- `shortages` owns the current remaining shortage quantity and validates proposal applicability against it;
- proposal correction is a shortage-domain action by the proposal author;
- acceptance must validate the proposal against the latest shortage state in the same application use case / transaction boundary;
- stale acceptance attempts must follow the existing conflict and reconciliation rules established in decisions 10.329–10.330;
- no warehouse-side automatic quantity mutation is performed.

MVP:
- a proposal that exceeds the current remainder is visibly marked as requiring correction before acceptance;
- acceptance action is unavailable until the proposal quantity is corrected;
- the proposal author can adjust the active proposal quantity and resubmit it for review.
