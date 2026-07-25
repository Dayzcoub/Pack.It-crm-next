# 25 Shortages 10.342

Decision: if the recovery mode contains no text fields, pressing `Остаться` in the close-confirmation dialog returns focus to the recovery-mode heading.

Behavior:
- closing the confirmation dialog keeps the recovery mode open;
- when at least one text field exists, focus follows decision 10.341 and moves to the first text field;
- when no text fields exist, the recovery-mode heading becomes the focus target;
- the heading must support programmatic focus without changing its visual or semantic role;
- screen readers announce the recovery-mode context after focus returns;
- no data is removed and no navigation occurs when the user chooses `Остаться`.

Architecture binding:
- focus restoration is transient accessibility behavior owned by `apps/web`;
- returning focus does not invoke `shortages.resolve`, `shortages.accept_proposal`, or any other application use case;
- it creates no shortage history, domain event, audit record, or notification;
- the recovery data remains client-side and limited to the current page session according to decision 10.332.

MVP:
- an empty recovery mode has a programmatically focusable heading;
- `Остаться` closes only the confirmation dialog;
- focus visibly and programmatically moves to that heading;
- keyboard navigation continues from the recovery-mode context;
- recovery data and the current shortage state remain unchanged.
