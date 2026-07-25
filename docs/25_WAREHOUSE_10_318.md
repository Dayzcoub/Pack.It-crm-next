# 25 Shortages 10.318

Decision: if the authorized resolver manually entered a general comment while using a result type without a mandatory explanation, that general comment is preserved when switching to a result type that requires a reason or explanation.

Behavior:
- the manually entered general comment remains unchanged in its own field;
- the assigned user's original proposal comment is separately inserted into the mandatory reason or explanation field;
- the two fields remain independent and editable;
- neither field overwrites the other during the result-type switch;
- the original proposal and its original comment remain unchanged in shortage domain history.

MVP:
- preserve manually entered general-comment draft state across the switch;
- prefill the mandatory field from the original proposal comment according to the existing transfer rules;
- validate the mandatory field independently before `shortages.resolve` may be submitted;
- store the final general comment and final reason or explanation as separate values;
- the submitted resolution remains a separate action, not proposal acceptance;
- no proposal-acceptance notification is emitted for the separate resolution.
