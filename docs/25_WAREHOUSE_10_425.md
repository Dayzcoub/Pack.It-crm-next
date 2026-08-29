# 25 Shortages 10.425

Decision: a user with `shortages.resolve` may directly resolve shortage quantity even when that quantity is currently reserved by an active proposal; the direct final resolution takes priority over the proposal reservation.

Behavior:
- an active proposal reservation does not block an authorized final resolution performed through `shortages.resolve`;
- if the direct resolution consumes quantity reserved by an active proposal, that affected proposal is automatically closed as no longer relevant;
- the proposal is not rewritten, reduced, or silently adapted to the new shortage remainder;
- closing the affected proposal releases its proposal reservation immediately;
- the closed proposal remains in shortage/proposal history together with the reason that another final resolution made it no longer relevant;
- the proposal author is notified under the existing rule for proposals automatically closed because another final resolution was accepted;
- the shortage remainder is recalculated only from successfully committed domain actions.

Architecture binding:
- `shortages.resolve` remains the higher-authority final-resolution use case;
- proposal reservation from 10.424 is a shortage-domain coordination mechanism, not a hard reservation against final resolution;
- `shortages` owns, in one transactional boundary, the direct resolution, affected proposal closure, reservation release, and resulting shortage state;
- acceptance or resolution commands must validate the latest shortage/proposal state before commit;
- `notifications` delivers only after the source action and automatic proposal closure succeed;
- `audit` independently records the significant final resolution and automatic proposal closure.

MVP:
- direct final resolution may override quantity reserved by an active proposal;
- every affected proposal is automatically closed rather than auto-adjusted;
- its reservation is released as part of the same successful domain transition;
- history preserves the proposal and explains why it was closed.
