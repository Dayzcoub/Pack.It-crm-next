# 25 Shortages 10.420

Decision: disabling a proposal author's account is equivalent to losing `shortages.propose_resolution`; the author's active proposals are automatically withdrawn under the same rules.

Behavior:
- when the author's account is disabled, every still-active proposal authored by that account is automatically withdrawn;
- this follows the same lifecycle rules established for loss of `shortages.propose_resolution` in decisions 10.413–10.419;
- withdrawn proposals remain in shortage history and are not restored automatically if the account is later re-enabled;
- if a warehouse user is currently reviewing one of those proposals, the proposal is withdrawn immediately, the review lock is released, and the open form becomes read-only with the withdrawal reason;
- the author-side notification rules are the same as for permission loss where delivery remains technically possible;
- the system records the withdrawal using the normal withdrawal classification with system as initiator and an automatically generated mandatory comment explaining that the author's account was disabled.

Architecture binding:
- account/authorization state change triggers the shortage-domain withdrawal use case for affected active proposals;
- `shortages` owns the proposal state transition and shortage history;
- `notifications` delivers only after successful withdrawal and only where a valid recipient channel still exists;
- `audit` independently records the account-status change and resulting proposal withdrawals;
- no active proposal authored by a disabled account may remain reviewable or acceptable.

MVP:
- disabling an account immediately removes its active proposals from the actionable review set;
- affected proposals remain visible in history as withdrawn by the system;
- re-enabling the account does not resurrect those proposals; a new proposal must be created if needed.
