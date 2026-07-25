# 25 Shortages 10.341

Decision: after the user chooses `Остаться` in the recovery-mode close confirmation, focus moves to the first text field shown in recovery mode.

Behavior:
- the confirmation dialog closes without deleting the recovered text data;
- focus moves to the first available text field in the recovery view;
- the field remains read-only, but its text can be selected and copied;
- the recovery view remains open in the same state;
- no navigation or new shortage action starts automatically.

Accessibility:
- focus transfer must be programmatic and predictable;
- keyboard users must immediately return to useful recovery content;
- screen readers must receive the focused field label and its read-only state;
- focus must not fall back to the page body or an unrelated control.

Architecture binding:
- dialog closing and focus restoration are transient `apps/web` presentation behavior;
- recovered text remains session-local according to the previously defined recovery rules;
- choosing `Остаться` does not invoke `shortages.resolve`, `shortages.accept_proposal`, or any other source-domain use case;
- no shortage history, audit event, notification, or persisted recovery record is created.

MVP:
- `Остаться` closes only the confirmation dialog;
- recovery data remains available;
- focus moves to the first recovery text field;
- no domain state changes occur.
