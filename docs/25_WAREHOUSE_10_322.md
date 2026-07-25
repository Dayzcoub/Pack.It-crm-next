# 25 Shortages 10.322

Decision: an error shown for a mandatory reason or explanation disappears immediately after the field value satisfies the active result's validation rules.

Behavior:
- after a failed submission, the form preserves all entered values and focuses the invalid field;
- validation is re-evaluated while the user corrects that field;
- the visible field error is removed as soon as the current value becomes valid;
- the user does not need to press `Save` again merely to clear the displayed error;
- switching result types applies the validation rules of the newly selected result;
- final submission is still validated by the `shortages.resolve` use case on the server.

MVP:
- perform responsive field-level revalidation after the first validation error;
- clear the error message and invalid visual state immediately when the field becomes valid;
- do not clear or modify other form values;
- keep the save action available for the actual submission;
- treat client-side validation as feedback only, not as a replacement for server-side validation.
