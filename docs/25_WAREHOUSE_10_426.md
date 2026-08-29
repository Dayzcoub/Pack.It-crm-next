# 25 Shortages 10.426

Decision: when a direct `shortages.resolve` action will affect quantity currently reserved by an active proposal and therefore close that proposal under 10.425, the resolver must explicitly confirm this consequence before the final save.

Behavior:
- the confirmation is shown before committing the direct shortage resolution;
- it must clearly state that an active proposal is currently reserving the affected shortage quantity;
- it must clearly state that proceeding will close the affected proposal as no longer relevant;
- cancelling the confirmation leaves the shortage and proposal unchanged;
- confirming allows the direct resolution to continue through the normal `shortages.resolve` use case;
- after successful resolution, the affected proposal is closed according to 10.425 and its reservation is released as part of the same resulting shortage-state transition;
- if the proposal or shortage state changes before commit, the use case must revalidate current state rather than rely only on the confirmation snapshot.

Architecture binding:
- `shortages` owns shortage state, proposal applicability, proposal reservation and proposal closure;
- the confirmation is a UI/application-flow safeguard and does not replace transactional domain validation;
- `shortages.resolve` must validate the current shortage/proposal state inside the same transaction boundary as the resolution;
- `notifications` and `audit` consume only successful resulting domain actions according to their existing rules.

MVP:
- direct resolution cannot silently displace an active proposal reservation;
- the resolver explicitly confirms that the proposal will be closed;
- no domain change occurs when the confirmation is cancelled.
