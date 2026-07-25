# 25 Shortages 10.388

Decision: withdrawing a proposal requires a comment, but no separate structured withdrawal-reason field is introduced.

Behavior:
- the responsible user enters a comment when withdrawing the proposal;
- the comment explains the withdrawal in free form;
- an empty comment does not allow the withdrawal action to be submitted;
- the comment is stored together with the withdrawal event in the shortage history;
- warehouse users can see the withdrawal comment from the proposal history and from the related notification context;
- a new proposal created later remains a separate proposal and does not overwrite the withdrawal comment.

Architecture binding:
- the withdrawal command belongs to the `shortages` bounded context;
- the withdrawal comment is part of the proposal-withdrawal domain record, not an `inventory` or `warehouse-operations` field;
- `notifications` delivers the warehouse notification only after the withdrawal transaction succeeds;
- `audit` records the withdrawal as a significant action independently from the shortage history.

MVP:
- one mandatory free-text comment field is sufficient;
- no reason classifier, reason catalog, or separate structured reason field is required;
- the withdrawn proposal remains immutable in history together with its comment.
