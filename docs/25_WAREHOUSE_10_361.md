# 25 Shortages 10.361

Decision: on touch devices, the full-text hint opened by a long press remains visible after the finger is released and closes only when the user taps outside the hint.

Behavior:
- a long press on a truncated project or section value opens a non-editable hint with the full value according to decision 10.360;
- releasing the finger does not close the hint;
- tapping outside the hint closes it;
- tapping or interacting inside the hint does not close it unless a dedicated close interaction is introduced by another decision;
- only one full-text hint may be open at a time;
- opening another truncated value replaces the currently open hint.

Accessibility:
- the hint must be associated programmatically with the truncated value that opened it;
- keyboard and assistive-technology users continue to receive the full value through focus-based disclosure and an accessible name or description;
- closing the hint returns focus or interaction context to the originating value when focus management is applicable.

Architecture binding:
- the open or closed hint state belongs only to transient `apps/web` UI state;
- displaying or closing the hint does not invoke a shortage command;
- it creates no shortage history, audit event, notification, or persisted domain state.

MVP:
- a long press opens the full-text hint;
- the hint remains open after release;
- a tap outside closes it;
- opening a different hint replaces the previous one;
- no domain side effects are produced.
