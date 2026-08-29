# Warehouse / Shortages — Decision 10.402

## Decision

If an author adjusts an active proposal to match the current remaining shortage quantity, the warehouse operator does **not** receive a separate notification solely because of that correction.

The proposal status and current values are updated in the interface and become available for normal review there.

## Domain implications

- The correction remains part of the proposal lifecycle owned by `shortages`.
- The updated proposal state must be visible to warehouse users through the normal shortage/proposal read model.
- This correction does not create a dedicated `notifications` delivery by itself.
- Normal audit/history requirements for proposal changes still apply where defined.
- This does not change the rule from 10.401: a proposal whose quantity exceeds the current remaining shortage cannot be accepted until the author corrects it.
