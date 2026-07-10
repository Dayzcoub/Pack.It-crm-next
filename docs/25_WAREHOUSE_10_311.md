# 25 Warehouse 10.311

Decision: if the transferred proposal comment is saved unchanged in a separate normal shortage action, history shows only the final comment text without a separate source marker.

Behavior:
- the temporary `Transferred from assigned user's proposal` label exists only inside the unsaved form;
- after the normal action is saved, the history entry contains the submitted comment as an ordinary final-action comment;
- history does not state that the comment was copied from the assigned user's proposal;
- the original proposal and its original comment remain separately visible in the card history;
- the final action remains a separate action, not proposal acceptance.

MVP:
- no transfer-source flag is displayed in the saved action history;
- the final comment is rendered the same way as any manually entered action comment;
- the original proposal event remains unchanged and provides the historical source context;
- editing or not editing the transferred text does not change this history rule;
- no proposal-acceptance notification is sent for the separate final action.
