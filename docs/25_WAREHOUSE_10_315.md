# 25 Shortages 10.315

Decision: when the confirmer switches from a result type with a mandatory reason or explanation field to a result type without such a field, any proposal comment that was auto-transferred into the mandatory field is discarded automatically.

Behavior:
- the transferred draft is removed when the result type changes to one without a mandatory reason or explanation;
- the general comment field remains empty;
- the discarded transferred text is not copied into any other field;
- the original proposal and its original comment remain unchanged in shortages history;
- the separate resolution is still executed through the `shortages.resolve` use case and requires `shortages.resolve` permission.

MVP:
- only auto-transferred proposal text is discarded by this rule;
- the new result form opens with no inherited proposal comment;
- no proposal-acceptance event or notification is created;
- server-side validation uses only the fields required by the newly selected result type;
- saving the separate resolution records only the final submitted data.
