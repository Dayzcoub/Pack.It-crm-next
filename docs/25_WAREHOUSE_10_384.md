# 25 Shortages 10.384

Decision: the full-value display interaction is considered complete and is no longer expanded within the current shortage-resolution design pass.

Behavior:
- decisions 10.374–10.383 define the active interaction model for showing a truncated project or section value;
- decisions 10.360–10.373 remain in documentation history but are superseded by decision 10.374;
- further tooltip, muted-popup, positioning, timing, gesture, and closing details are deferred unless implementation reveals a concrete usability or accessibility issue;
- the requirements workflow returns to the main shortage-resolution lifecycle.

Architecture binding:
- this completion marker changes no shortage domain state or command behavior;
- the interaction remains transient `apps/web` presentation behavior;
- no shortage history, audit event, or notification is created by opening, replacing, copying from, or closing the muted popup.

MVP:
- implement the interaction according to decisions 10.374–10.383;
- do not introduce additional popup mechanics without a documented product need;
- continue specification with the core shortage workflow.
