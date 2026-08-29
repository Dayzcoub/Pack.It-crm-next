# Warehouse 10.424 — Active proposals reserve shortage quantity

## Decision

An active proposal temporarily reserves the corresponding quantity of the shortage.

While the proposal remains active:

- its proposed quantity is treated as reserved against the current shortage remainder;
- other authors may create proposals only against the unreserved remainder;
- the same shortage quantity must not be simultaneously reserved by multiple active proposals;
- changing, withdrawing, auto-withdrawing, accepting, or otherwise closing the proposal recalculates and releases or converts its reservation as part of the same shortage-domain state transition;
- reservation is a shortage-domain coordination rule, not an inventory balance mutation and not a stock reservation in the `reservations` bounded context.

`shortages` owns the reservation accounting for proposal quantities and must validate proposal creation/editing against the latest open and unreserved shortage quantity in the transaction that saves the proposal.

## Context

This decision changes the earlier competitive-proposal assumption: active proposals are no longer purely advisory against the full remaining shortage. They consume proposal capacity until they are changed or closed, preventing multiple authors from proposing solutions for the same units at the same time.
