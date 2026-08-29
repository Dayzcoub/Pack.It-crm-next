# 10.457 — Subrent is project-only and never enters warehouse stock

## Decision

Subrented equipment is **not part of PACK.IT warehouse inventory at any point**.

It exists only in the context of the specific project and the specific demand/shortage it was arranged to cover.

Typical flow:

`Project demand → Subrent arranged → Equipment delivered to event/site → Used on project → Returned directly to owner/supplier`

## Consequences

- Subrent never increases company-owned stock.
- Subrent never enters `on_hand`, `available`, `stock_addition`, or any other warehouse balance.
- Subrent is not issued from or returned to PACK.IT warehouse as a normal warehouse operation.
- Subrent must remain linked to its project and supplier/owner.
- The operational equipment-location view may show subrent while it is active on a project, but this is a project/logistics projection, not inventory ownership.
- After the event, subrented equipment leaves the project flow by returning to its owner/supplier.

## Relation to shortage resolution

A confirmed subrent may satisfy a project's unmet demand, but it does so as an external project supply source, not by modifying inventory.

This decision clarifies and supersedes any interpretation of 10.454–10.456 that could imply temporary inclusion of subrent in warehouse stock.
