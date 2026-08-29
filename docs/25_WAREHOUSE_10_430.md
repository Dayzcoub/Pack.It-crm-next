# 25 Shortages 10.430

Decision: use a unified shortage-exception model based on one `ShortageCase`, multiple resolution proposals, and one common exception workflow. FIFO is only a UI sorting preference and is not a domain restriction.

Canonical model:
- one shortage is represented by one `ShortageCase`;
- users with `shortages.propose_resolution` may add resolution proposals to the case;
- proposals are alternatives for resolving the shortage, not reservations and not independent shortage records;
- proposals do not change the shortage quantity and do not reserve any part of it;
- the shortage remainder changes only after a resolution is actually accepted/applied;
- every proposal is revalidated against the latest shortage state when it is accepted;
- if a proposal is no longer applicable to the current remainder, the existing stale / `requires adjustment` rules apply;
- when a shortage is fully resolved, remaining active proposals are closed as no longer relevant and preserved in history;
- partial resolution recalculates the remaining shortage and the applicability of still-active proposals;
- concurrency protection remains focused on preventing conflicting simultaneous state-changing actions, not on proposal ordering.

Workflow:
- `OPEN` — shortage exists and still requires resolution;
- `RESOLVING` — one or more resolution actions/proposals are being worked on;
- `PARTIALLY_RESOLVED` — one or more accepted actions reduced the shortage but an open remainder still exists;
- `RESOLVED` — no unresolved shortage remainder remains.

Proposal ordering:
- proposals may be displayed oldest-first by default for operational convenience;
- creation time does not give a proposal exclusive priority or a right to be accepted before later proposals;
- a warehouse user may choose any currently applicable proposal they are authorized to accept;
- FIFO must not block a better or more appropriate later proposal.

Superseded decisions:
- 10.428 is superseded insofar as it introduced business priority by creation time; oldest-first remains UI sorting only;
- 10.429 is fully superseded; there is no strict FIFO acceptance lock between proposals;
- 10.427 remains the canonical rule that proposals do not reserve shortage quantity and already supersedes the reservation branch 10.424–10.426.

Architecture binding:
- `shortages` owns `ShortageCase`, proposal lifecycle, current shortage remainder, proposal applicability, and shortage-domain history;
- named application use cases perform proposal acceptance/resolution with transactional validation against the latest PostgreSQL state;
- `notifications` reacts only after successful source-domain transitions where an existing notification rule requires delivery;
- `audit` independently records significant state-changing actions;
- role names do not grant authority by themselves; canonical permissions remain authoritative.

MVP:
- implement one shortage-case workflow rather than separate reservation/queue mechanisms;
- proposals are non-reserving alternatives;
- oldest-first sorting is allowed in the UI but never enforced as an acceptance prerequisite;
- state-changing actions always validate against the current shortage remainder in the same transaction.
