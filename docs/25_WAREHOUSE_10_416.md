# 25 Shortages 10.416

Decision: if the author loses `shortages.propose_resolution` while a warehouse user is already reviewing that proposal and holds its review lock, the proposal is closed immediately rather than waiting for the current review to finish.

Behavior:
- loss of `shortages.propose_resolution` invalidates the author's active proposals immediately according to decision 10.413;
- an active warehouse review lock does not delay that invalidation;
- the affected proposal is automatically closed and remains in shortage/proposal history;
- the active proposal-review lock is released;
- an already-open warehouse review form switches to read-only state;
- the form explains that the proposal is no longer valid because the author lost permission to submit shortage-resolution proposals;
- no acceptance or other final-resolution action may be completed from that stale review form;
- the author notification rule from decision 10.415 still applies.

Architecture binding:
- `shortages` owns proposal validity, automatic closure, and release of the proposal-specific review lock;
- permission loss must be applied against the latest authorization state before proposal acceptance can commit;
- `notifications` sends the author notification only after successful proposal closure;
- `audit` records the permission-driven automatic closure independently;
- no delayed "finish current review first" exception is introduced.

MVP:
- permission revocation immediately closes affected active proposals;
- open warehouse review UI updates to read-only and shows the closure reason;
- the released lock becomes available according to the existing real-time lock-state rules.
