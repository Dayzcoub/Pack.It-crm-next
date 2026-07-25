# 25 Shortages 10.343

Decision: after the user confirms closing the recovery mode, focus returns to the card or row of the current shortage.

Behavior:
- confirming `Close` removes the transient recovery data and closes the recovery interface;
- the shortages view remains on the refreshed current state established after the conflict;
- keyboard focus moves to the card or table row representing the same shortage;
- the focused shortage item must be scrolled into view when it is outside the visible area;
- focus does not move automatically to the action button inside the shortage item;
- the user can review the current shortage state before choosing any further action.

Architecture binding:
- focus restoration, scrolling, and recovery-data cleanup are transient `apps/web` presentation behavior;
- closing recovery mode does not invoke `shortages.resolve`, `shortages.accept_proposal`, or another source-domain command;
- no shortage history, audit record, domain event, side effect, or notification is created by this UI transition;
- the displayed shortage card or row is based on the refreshed server-backed read projection, not on the discarded form snapshot.

Accessibility:
- the card or row must be programmatically focusable without changing its normal tab order when not focused programmatically;
- its accessible name must identify the shortage sufficiently for the user to understand where focus moved;
- screen-reader users must be able to discover the refreshed shortage status from the focused item;
- focus must not be lost to the document body after the recovery overlay is removed.

MVP:
- confirmed closing deletes the current-session recovery snapshot;
- the recovery mode closes;
- focus returns to the same shortage card or row;
- the item is brought into view when necessary;
- no domain state changes as a result of focus restoration.
