# 25 Shortages 10.340

Decision: the cancel button in the recovery-mode close confirmation is labeled `Остаться`.

Behavior:
- the confirmation contains the primary action `Закрыть` and the cancel action `Остаться`;
- `Остаться` closes only the confirmation dialog;
- the recovery mode remains open;
- all recoverable text fields remain available in read-only form;
- no data is deleted when the user chooses `Остаться`;
- the same label is used for both populated and empty recovery modes.

Architecture binding:
- the confirmation dialog and the `Остаться` action are transient `apps/web` interface state;
- choosing `Остаться` does not invoke `shortages.resolve`, `shortages.accept_proposal`, or any other application use case;
- no shortage state, domain history, audit record, side effect, or notification is created;
- recoverable text remains limited to the current page session according to the previously accepted recovery rules.

MVP:
- the cancel button is visibly labeled `Остаться`;
- pressing it returns the user to the unchanged recovery mode;
- all displayed recovery text remains intact;
- repeated open-and-cancel cycles do not mutate domain or persisted application state.
