# 10.410 — Status recovery after shortage remainder increases again

## Decision

If an active proposal was marked **«требует корректировки»** because its quantity exceeded the then-current shortage remainder, that status is **not removed automatically** even if the shortage remainder later increases and the proposal quantity would again fit within it.

The proposal author must explicitly reopen and save the proposal again to confirm that the proposal is still current and intentional.

## Rules

- A proposal in **«требует корректировки»** remains unavailable for acceptance until the author confirms it again.
- A later increase in the shortage remainder does not silently reactivate the proposal.
- Re-saving the proposal creates the next current version under the existing proposal versioning rules from 10.403 and 10.405.
- The proposal type remains immutable under 10.406.
- No separate mandatory change reason is required under 10.407.
- This rule prevents an old proposal from becoming actionable again solely because surrounding shortage state changed.

## Domain boundary

This is shortage/proposal state logic owned by `shortages`. It must not create inventory, reservation, subrent, warehouse-operation, notification, or audit side effects merely because the remainder increased.
