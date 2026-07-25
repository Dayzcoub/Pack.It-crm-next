# 25 Shortages 10.370

Decision: successful recognition of a long press provides system haptic feedback when the device and browser support it.

Behavior:
- haptic feedback occurs only after the long press has been successfully recognized;
- the feedback accompanies opening the full-text tooltip;
- no vibration is triggered for an ordinary short tap or for a cancelled gesture;
- when the platform does not support haptic feedback, the tooltip still opens normally without showing an error;
- the implementation uses the available system or browser feedback mechanism and does not emulate vibration visually or acoustically.

Architecture binding:
- this is transient interaction behavior owned by `apps/web`;
- haptic support is treated as an optional progressive enhancement;
- the behavior does not alter shortage data or read projections;
- it invokes no shortage command and creates no shortage history, audit event, or notification.

MVP:
- supported touch devices provide haptic confirmation after successful long-press recognition;
- unsupported devices fall back silently to visual tooltip opening;
- cancelled gestures produce no haptic feedback.
