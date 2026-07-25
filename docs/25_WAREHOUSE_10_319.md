# 25 Shortages 10.319

Decision: when an authorized user switches between different result types that both require a mandatory reason or explanation, any already edited transferred text is preserved in the mandatory field.

Behavior:
- the current edited value remains in the mandatory field after the result type changes;
- the original proposal comment is not inserted again automatically;
- the preserved text remains editable and is validated against the newly selected result type;
- if the new result requires different or additional validation, submission is blocked until those rules are satisfied;
- the general comment remains independent and is not overwritten;
- the final action is executed through the `shortages.resolve` use case and remains separate from proposal acceptance.

MVP:
- preserve the edited mandatory-text draft when switching between result types that both require such a field;
- do not restore or duplicate the original proposal comment during that switch;
- retain normal unsaved-change handling for leaving the form or switching to a result without a mandatory field;
- save only the final submitted value in shortage domain history;
- keep notification delivery and audit logging as separate post-transaction effects.
