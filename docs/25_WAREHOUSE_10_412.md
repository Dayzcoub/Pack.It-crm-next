# 25 Shortages 10.412

Decision: only the author of an active shortage-resolution proposal may edit that proposal.

Behavior:
- an active proposal remains associated with its original author;
- only that author may change the proposal while it is still editable under the existing lifecycle rules;
- another user does not gain edit rights merely by having `shortages.propose_resolution`;
- users with proposal permissions may create their own proposals, but they cannot mutate another author’s active proposal;
- warehouse review locks and the edit restrictions from decisions 10.389 and 10.404 continue to apply in addition to this ownership rule;
- proposal history must continue to identify the author of each version.

Architecture binding:
- `shortages` owns proposal authorship and enforces author-only mutation;
- `shortages.propose_resolution` authorizes proposing a resolution, but does not grant cross-author edit authority;
- authorization must validate both the permission and proposal ownership in the same application use case before mutation;
- `audit` records significant proposal edits independently from the shortage-domain history.

MVP:
- edit controls are available only to the proposal author when the proposal is otherwise editable;
- other authorized users see the proposal read-only and may submit a separate proposal if the shortage still allows it.
