# 25 Warehouse 10.308

Decision: when a proposal comment is copied into the normal shortage action form through `Choose another result`, the form must visibly indicate that the text came from the assigned user's proposal.

Behavior:
- the copied comment appears in the normal comment field as editable draft text;
- a small label is shown near the field: `Transferred from assigned user's proposal`;
- the label is informational and does not prevent editing or deleting the text;
- if the copied text is completely removed, the transfer label is no longer needed;
- the original proposal and its original comment remain unchanged in history.

MVP:
- the source label appears only when proposal comment text was actually transferred;
- the label is visually secondary and does not look like a status;
- the transferred text can be changed or deleted before saving;
- the final action stores only the final submitted comment;
- the action remains a separate final action, not proposal acceptance.
