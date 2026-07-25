# 25 Shortages 10.326

Decision: after the user corrects the final validation error, the form does not submit automatically. The user must explicitly press `Save` again.

Behavior:
- correcting the final invalid field removes the field error according to the previously defined live-validation rules;
- the form remains open with all entered values preserved;
- no shortage resolution or proposal-acceptance use case is executed automatically;
- the user reviews the corrected form and explicitly presses `Save`;
- submission then runs the complete client and server validation again.

MVP:
- successful field correction never triggers an automatic write;
- the explicit save action remains the only user intent that starts the controlled `shortages` application use case;
- duplicate clicks and repeated submissions are handled by the normal pending-state and idempotency rules;
- if validation fails again, the form follows the previously defined top-to-bottom focus and scroll behavior;
- domain history, audit, side effects, and notification events are created only after a successful explicit save.
