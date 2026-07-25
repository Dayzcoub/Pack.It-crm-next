# 25 Shortages 10.320

Decision: when an edited or transferred mandatory explanation is carried into another shortage result type, any result-specific validation error is shown only when the user attempts to save the separate resolution action.

Behavior:
- switching result types does not immediately block the form or display a validation error for the preserved explanation;
- the user may continue editing the selected result and its fields;
- the `shortages.resolve` use case validates the final explanation against the selected result type when submission is attempted;
- if the explanation is invalid, the action is not saved and no domain event, notification, audit entry, or cross-context effect is produced;
- all entered form data remains available for correction after the failed submission.

MVP:
- do not run result-specific explanation validation as a blocking action during result selection;
- validate the final selected result and explanation on submit;
- show the validation error next to the mandatory explanation field;
- preserve the selected result, mandatory explanation, and general comment after the error;
- create the shortage history event and downstream effects only after successful validation and transaction completion.
