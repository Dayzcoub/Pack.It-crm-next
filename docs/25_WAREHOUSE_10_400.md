# 25 Shortages 10.400

Decision: when a shortage is only partially resolved, other active proposals remain active if they can still apply to the remaining unresolved quantity.

Behavior:
- accepting one proposal may reduce the open shortage quantity without fully closing the shortage;
- proposals that can still cover some or all of the remaining quantity remain active;
- proposals that are no longer applicable to the remaining shortage quantity may be closed as no longer relevant;
- all proposal state changes remain visible in shortage history;
- once the shortage is fully resolved, remaining active proposals are closed as no longer relevant according to decision 10.398.

Architecture binding:
- `shortages` owns recalculation of the remaining unresolved quantity and proposal applicability;
- proposal applicability is evaluated against the current shortage state after each successful partial resolution;
- `notifications` may notify affected proposal authors only after the corresponding proposal state change succeeds;
- `audit` remains independent from shortage domain history.

MVP:
- partial resolution does not automatically invalidate every other proposal;
- still-applicable proposals remain available for subsequent resolution of the remainder;
- fully resolving the shortage closes the remaining proposals according to decision 10.398.
