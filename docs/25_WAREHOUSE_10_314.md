# 25 Shortages 10.314

Decision: when an authorized user leaves proposal acceptance and chooses another result whose form has no mandatory reason or explanation field, the assigned user's proposal comment is not transferred anywhere.

Behavior:
- the separate shortage resolution form opens with an empty general comment field;
- the proposal comment is not copied into the general comment field or any hidden draft state;
- the user may enter a new general comment manually;
- the original proposal and its original comment remain unchanged in the shortage domain history;
- the separate resolution is executed through the `shortages.resolve` use case and requires `shortages.resolve` permission.

MVP:
- automatic comment transfer occurs only for result types with a mandatory reason or explanation field, as defined previously;
- result types without such a field open with no transferred text;
- cancelling the separate resolution does not modify the original proposal;
- saving creates a separate shortage resolution event, not proposal acceptance;
- no proposal-acceptance notification is emitted for the separate resolution;
- notifications and audit effects remain separate from the `shortages` domain state change.
