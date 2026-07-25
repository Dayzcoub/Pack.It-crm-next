# 25 Shortages 10.317

Decision: after the user confirms deletion of edited transferred text, switches to a result without a mandatory reason or explanation, and later selects a result that requires such a field, the original proposal comment is transferred into the required field again.

Behavior:
- the previously edited and discarded draft is not restored;
- the transfer is performed again from the unchanged original proposal comment;
- the required field receives a fresh editable draft;
- the transfer-source label is shown again because a new transfer has occurred;
- the normal validation rules for the newly selected result remain active;
- the original proposal and its original comment remain unchanged in shortage history.

Architecture:
- the draft transfer belongs to the `shortages` form flow;
- the source is the original proposal stored by the `shortages` context;
- no new shortage history event, audit entry, or notification is created until the separate resolution action is submitted successfully;
- submitting the final result requires `shortages.resolve` and any additional permission required by the selected cross-context effect.

MVP:
- each new selection of a result with a mandatory reason or explanation may initiate a fresh transfer from the original proposal;
- discarded user edits are never recovered automatically;
- the fresh transfer restores the temporary source-label state;
- cancelling the form does not modify the proposal or create a resolution action.
