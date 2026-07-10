# 25 Warehouse 10.306

Decision: if the confirmer has already changed data in the `Accept proposal` form, clicking `Choose another result` requires a confirmation warning before those changes are discarded.

Behavior:
- if the acceptance form still matches the original proposal, `Choose another result` opens the normal shortage action without an extra warning;
- if any proposal data has been changed, the system asks for confirmation;
- the warning states that unsaved changes in the acceptance form will be lost;
- after confirmation, the acceptance form is closed and the normal shortage action opens;
- if the user cancels, the acceptance form remains open with all current changes preserved.

MVP:
- the warning appears only when unsaved changes exist;
- the confirmation offers clear continue and cancel actions;
- continuing discards all acceptance-form changes, including the adjustment reason;
- cancelling preserves the current form state;
- the original proposal remains unchanged and visible in history.
