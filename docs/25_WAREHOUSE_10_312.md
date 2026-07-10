# 25 Warehouse 10.312

Decision: when the confirmer chooses another result whose form requires a mandatory reason or explanation, the assigned user's proposal comment is automatically inserted into that required field as editable draft text.

Behavior:
- the selected result determines whether a mandatory reason or explanation field exists;
- if such a field exists, the proposal comment is copied into it automatically;
- the copied text remains fully editable and may be replaced before saving;
- the field is still validated by the normal rules for the selected result;
- if the proposal has no comment, the required field remains empty and must be completed manually;
- the original proposal and its original comment remain unchanged in history.

MVP:
- automatic transfer occurs only after a result with a mandatory reason or explanation is selected;
- transferred text is treated as unsaved draft content;
- saving is blocked if the required field is empty after editing or deletion;
- the temporary source label follows the previously defined transferred-comment rules;
- the final action stores only the final submitted reason or explanation;
- the action remains a separate final action, not proposal acceptance.
