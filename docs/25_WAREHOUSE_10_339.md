# 25 Shortages 10.339

Decision: the confirming button used to close the recovery mode is labeled `Закрыть`.

Behavior:
- the confirmation dialog uses the neutral primary action label `Закрыть`;
- the dialog text explicitly explains that closing the recovery mode permanently removes the retained draft data from the current page session;
- the secondary action cancels the close operation and returns the user to the recovery mode without changing its contents;
- confirming the close removes the temporary recovery data and closes the recovery view;
- the same button label is used whether the recovery mode contains text or is empty.

Architecture binding:
- the confirmation dialog, its wording, and temporary recovery data are transient `apps/web` interface state;
- closing the recovery mode does not invoke `shortages.resolve`, `shortages.accept_proposal`, or another source-domain command;
- closing does not modify the shortage, proposal, domain history, audit records, or notifications;
- no server-side persistence is required for recovery data that exists only in the current page session.

MVP:
- the confirmation button is labeled `Закрыть`;
- the warning text clearly states that retained data will be deleted and cannot be restored;
- canceling preserves the recovery mode and its data;
- confirming closes the recovery mode and deletes its temporary data;
- the behavior is identical for populated and empty recovery modes.
