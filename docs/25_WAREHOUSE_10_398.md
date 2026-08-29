# 25 Shortages 10.398

Decision: when one proposal is accepted as the final resolution for a shortage, all other active proposals for the same shortage are automatically closed as no longer relevant.

Behavior:
- the accepted proposal becomes part of the final shortage resolution flow;
- all other still-active proposals for that same shortage are closed automatically;
- automatically closed proposals remain available in shortage history;
- they are not deleted, merged into the accepted proposal, or treated as withdrawn by their authors;
- their closure reason is that another proposal has already become the final resolution;
- closed proposals can no longer be accepted or edited as active proposals.

Architecture binding:
- `shortages` owns the proposal lifecycle and automatic closure of competing active proposals after a final resolution;
- proposal-history changes are persisted with the shortage domain history;
- `audit` may record the significant final-resolution action separately according to the system audit policy;
- `notifications` deliver only after the final-resolution transaction succeeds.

MVP:
- accepting one proposal as the final result automatically closes all other active proposals for the shortage as no longer relevant;
- those proposals remain visible in history with their final status.
