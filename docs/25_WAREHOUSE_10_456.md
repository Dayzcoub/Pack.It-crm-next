# 10.456 — Subrent equipment belongs to a specific project

## Decision

For the MVP, subrented equipment is always linked to the specific project / demand for which it was ordered.

It does **not** become part of a temporary shared warehouse pool while it is physically with the company.

## Rules

- Every subrent quantity must reference its owning project or project demand.
- Subrent can cover a shortage or another explicitly approved need for that project.
- Subrent equipment may appear in the common operational register "Где оборудование" together with owned equipment, but must be clearly marked as `Subrent` and show its external owner / supplier.
- Presence of subrent equipment at the warehouse, venue, or with a crew does not make it available for unrelated projects.
- Availability calculations for other projects must ignore subrent assigned to another project.
- Reassignment of subrent to another project, if ever needed, is a separate explicit business action and is outside the MVP baseline.

## Rationale

This keeps subrent predictable for event planning: external equipment is procured to satisfy a concrete project need rather than acting as an opportunistic temporary stock pool.
