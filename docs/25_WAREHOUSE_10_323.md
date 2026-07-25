# 25 Shortages 10.323

Decision: after the user fixes the currently focused validation error, if another field in the same shortage action form is still invalid, focus automatically moves to the next invalid field.

Behavior:
- the current error disappears as soon as the corrected field passes validation;
- if another invalid field remains, the form moves focus to it automatically;
- the next field is selected according to the visible form order;
- all entered values remain unchanged;
- focus movement does not submit or otherwise modify the action.

MVP:
- automatic focus movement occurs only after the current field becomes valid;
- hidden or inactive fields are skipped;
- the next focused field shows its existing validation message;
- if no validation errors remain, focus stays in the corrected field;
- server-side validation remains authoritative when the action is submitted.
