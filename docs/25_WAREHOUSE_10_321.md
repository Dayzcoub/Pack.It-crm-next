# 25 Shortages 10.321

Decision: after mandatory explanation validation fails, the form preserves all entered data and moves focus to the invalid field.

Behavior:
- submission is blocked while the explanation fails validation;
- no entered form values are cleared or reset;
- the invalid mandatory explanation field receives focus;
- the validation message is shown next to that field;
- the user can correct the value and submit again without rebuilding the action.

Architecture:
- client-side feedback may focus and highlight the field;
- the `shortages.resolve` use case remains the authoritative validation boundary;
- a failed validation attempt creates no shortage resolution, domain-history entry, notification event, or audit action.

MVP:
- preserve result type, quantities, explanation, general comment, and other draft values;
- focus the first invalid field after a failed submission;
- keep the form open in its current state;
- clear the error only after the field becomes valid or the action is cancelled;
- submit the final action only after all server-side validation succeeds.
