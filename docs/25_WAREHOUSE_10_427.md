# 25 Shortages 10.427

Decision: shortage-resolution proposals do not reserve shortage quantity. The shortage remainder changes only when a resolution is actually accepted/applied.

Behavior:
- an active proposal is advisory and does not reduce the quantity available to other proposals;
- multiple proposals may therefore overlap in quantity while the shortage remains unresolved;
- proposal creation/editing validates against the current shortage state for basic applicability, but does not create a reservation;
- when a proposal is accepted, `shortages` must revalidate the latest shortage remainder and proposal applicability in the same transaction boundary;
- if the proposal still fits the current remainder, it may be accepted normally or partially according to the existing rules;
- if it no longer fits, the existing stale/`requires adjustment` rules apply;
- if the shortage has already been fully resolved by another action, the proposal is closed as no longer relevant;
- direct resolution through `shortages.resolve` does not need to override or release proposal reservations because such reservations no longer exist.

Superseded decisions:
- 10.424 is superseded: active proposals no longer reserve shortage quantity;
- 10.425 is superseded to the extent that it described priority over a proposal reservation; direct resolution remains allowed under the existing final-resolution rules, but there is no reservation to override;
- 10.426 is superseded to the extent that it required confirmation specifically because a reservation would be displaced; any proposal closure caused by a final resolution follows the normal proposal-obsolescence rules instead.

Architecture binding:
- `shortages` remains the source of truth for shortage remainder, proposal applicability, and proposal lifecycle;
- proposal state and shortage quantity are separate concepts;
- acceptance/final-resolution use cases validate the latest state transactionally before changing the shortage remainder;
- no reservation aggregate, allocation ordering, reservation priority, or reservation-release workflow is introduced for proposals;
- `audit` independently records significant accepted resolutions and automatic proposal closures.

MVP:
- proposals never reserve shortage quantity;
- shortage remainder changes only after accepted/applied resolution;
- overlapping active proposals are allowed across different authors;
- stale proposals use the existing `requires adjustment` and reconciliation rules;
- 10.424–10.426 are inactive where they depend on proposal reservation semantics.
