# 25 Shortages 10.428

Decision: when one shortage has multiple active proposals from different authors, proposal review priority follows proposal creation time: earlier proposals are considered before later proposals.

Behavior:
- active proposals are ordered by their creation timestamp from oldest to newest;
- the earlier active proposal has review priority over later active proposals for the same shortage;
- proposal priority does not reserve shortage quantity and does not change the shortage remainder by itself;
- actual shortage remainder still changes only after an accepted/final resolution under decision 10.427;
- if an earlier proposal becomes withdrawn, closed, invalid, or otherwise unavailable for consideration, the next active proposal becomes first in priority order;
- proposal ordering must remain deterministic and stable for the same persisted creation data.

Architecture binding:
- `shortages` owns proposal lifecycle and the canonical ordering of active proposals for a shortage;
- proposal creation time is persisted as domain data and used to determine review priority;
- this priority rule does not create an inventory-style reservation and must not mutate balances or shortage quantity;
- acceptance/resolution still validates the latest shortage state in its transaction boundary.

MVP:
- active proposals for one shortage are shown and processed in oldest-first order;
- later proposals remain active but are behind earlier active proposals in review priority;
- when an earlier proposal leaves the active set, the next proposal advances automatically.
