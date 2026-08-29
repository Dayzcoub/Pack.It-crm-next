# 25 Shortages 10.422

Decision: authorship of an active proposal cannot be transferred to another user.

Behavior:
- an active proposal remains permanently associated with the user who originally created it;
- neither an administrator nor another user can reassign the proposal author;
- if the original author can no longer maintain the proposal, the existing proposal must be withdrawn under the applicable withdrawal rules;
- another authorized user may then create a new proposal for the still-open shortage;
- the withdrawn proposal remains in shortage history with its original author snapshot and withdrawal details;
- the replacement proposal is a separate proposal with its own author, lifecycle, history, and review state.

Architecture binding:
- `shortages` owns proposal authorship and proposal lifecycle;
- proposal authorship is immutable after creation;
- `shortages.propose_resolution` authorizes creation of a new proposal but does not authorize reassignment of an existing proposal;
- withdrawal and replacement are explicit domain actions rather than an implicit ownership transfer;
- `audit` records the significant withdrawal/new-proposal actions independently.

MVP:
- there is no transfer-author action for active proposals;
- if a proposal must be continued by another person, the UI follows the withdraw-and-create-new flow;
- history keeps the original proposal and the replacement proposal as separate records.
