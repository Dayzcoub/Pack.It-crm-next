# 25 Shortages 10.331

Decision: when a shortage-resolution form is closed because the shortage was changed by another action and the original submission is no longer applicable, the user's unsaved form data remains available in a separate read-only view so that useful text can be copied.

Behavior:
- the conflicting action form closes and cannot be submitted again in its previous state;
- the current shortage state is shown as the authoritative result;
- the values entered in the closed form are displayed separately in read-only mode;
- the user may select and copy text from this view, but cannot edit or submit it;
- opening a new resolution action starts from the current shortage state and does not automatically restore the obsolete form values;
- the read-only view must clearly distinguish obsolete draft data from the current shortage data.

Architecture binding:
- conflict detection and the current shortage state are provided by the `shortages` bounded context;
- the read-only representation of unsaved values is transient UI state owned by `apps/web`;
- obsolete form data is not written to `shortages` domain history and does not create an audit event;
- no notification is emitted for merely displaying or copying the discarded draft;
- any new resolution remains a separate command and requires `shortages.resolve`.

MVP:
- after a conflict, the obsolete form cannot be resubmitted;
- all previously entered values remain visible in a clearly labeled read-only view;
- text can be selected and copied;
- the current shortage state remains visually separate and authoritative;
- starting a new action uses a clean form based on the current shortage state.
