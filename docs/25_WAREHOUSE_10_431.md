# 25 Shortages 10.431

Decision: accepting a proposal and applying a direct shortage resolution use one canonical domain mechanism: `ResolutionAction`.

Behavior:
- every effective change that reduces or closes a shortage is represented by a `ResolutionAction`;
- the source of the action is recorded explicitly, at minimum as `proposal` or `direct`;
- proposal acceptance does not use a separate shortage-mutating mechanism;
- direct resolution does not use a parallel domain path with different shortage semantics;
- both paths validate the latest shortage state and current applicability before applying the action;
- both paths update the shortage remainder through the same domain rules;
- partial and full resolution semantics are identical regardless of source;
- resulting shortage history stores the applied resolution action and its source;
- proposal-specific lifecycle effects, such as marking the accepted proposal and re-evaluating other active proposals, occur around the same canonical resolution action rather than replacing it.

Architecture binding:
- `shortages` owns `ResolutionAction`, shortage state transitions, proposal re-evaluation, and shortage-domain history;
- the application layer may expose separate use cases for accepting a proposal and resolving directly, but both delegate the actual shortage mutation to the same canonical resolution operation;
- authorization remains distinct by entry path: proposal acceptance requires the appropriate acceptance permission, while direct resolution requires `shortages.resolve`;
- permission differences must not create different shortage accounting semantics;
- the action must be applied transactionally against the latest shortage state;
- `notifications` react only after successful source-domain completion;
- `audit` independently records the significant action and its actor/source.

MVP:
- one `ResolutionAction` model is used for all accepted shortage resolutions;
- `source = proposal | direct` distinguishes how the resolution originated;
- there is no duplicated shortage-mutation logic for the two entry paths.
