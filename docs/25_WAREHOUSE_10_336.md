# 25 Shortages 10.336

Decision: the read-only recovery mode shown after a conflicting shortage update does not provide a separate “Create new action” button.

Behavior:
- the recovery mode is limited to preserving the relevant text fields for manual review and copying;
- the user explicitly closes the recovery mode before starting another shortage action;
- starting a new action remains part of the normal current-shortage interface and is not embedded into the recovery mode;
- closing the recovery mode follows the confirmation rule from decision 10.333 because the transient recovered text is deleted afterwards;
- after the recovery mode is closed, any new action starts from the current authoritative shortage state and a clean form;
- recovered text is never automatically transferred into the new action.

Architecture binding:
- the recovery mode and its temporary text snapshot are transient `apps/web` state;
- the snapshot is not stored in `shortages` domain history, `audit`, or any server-side draft storage;
- the normal shortage action entry point reloads the current shortage projection before opening a new form;
- submission of a new final action continues through `shortages.resolve` and requires the applicable permission;
- the conflict and recovery interface do not modify the original proposal or the action that changed the shortage.

MVP:
- no “Create new action” control is displayed inside the recovery mode;
- the user may manually copy the displayed text and then close the recovery mode;
- confirmed closure permanently removes the transient recovered text;
- a subsequent action is opened separately from the current shortage interface;
- no recovered value is automatically reused in that action.
