# 25 Warehouse 10.313

Decision: when the assigned user's proposal comment is transferred into a mandatory reason or explanation field for another result, it is not duplicated into the general comment field.

Behavior:
- the proposal comment is inserted only into the mandatory reason or explanation field required by the selected result;
- the general comment field remains empty unless the confirmer fills it manually;
- the transferred text remains editable and may be replaced or deleted;
- normal validation still requires the mandatory field to contain a valid value before saving;
- the original proposal and its original comment remain unchanged in history.

MVP:
- the system never auto-fills both fields with the same proposal comment;
- the general comment field is independent from the mandatory reason or explanation field;
- editing or deleting the transferred text follows the previously defined source-label rules;
- the final action stores each submitted field separately;
- the action remains a separate final action, not proposal acceptance.
