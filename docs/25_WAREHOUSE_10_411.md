# Warehouse 10.411 — Reconfirming a proposal without field changes

## Decision

A proposal marked as **requires adjustment** may be reopened and saved by its author without changing any proposal fields.

The save itself is treated as an explicit confirmation that the proposal is still current and applicable to the present shortage remainder.

After a successful save:

- the **requires adjustment** status is removed;
- the proposal returns to its normal active state;
- the proposal becomes available for review again, subject to the existing proposal lock rules;
- no artificial field change is required merely to reconfirm applicability.

This reconfirmation is still a meaningful state transition and should be preserved in the proposal/shortage history so that it is possible to distinguish automatic invalidation from later author confirmation.

## Context

This decision extends 10.409–10.410. A proposal that became oversized remains explicitly stale until its author confirms it again; however, once the current shortage remainder makes the same unchanged values valid again, the author does not need to modify data just to clear the stale marker.
