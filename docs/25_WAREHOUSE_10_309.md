# 25 Warehouse 10.309

Decision: the `Transferred from assigned user's proposal` label disappears after the confirmer first edits the transferred comment.

Behavior:
- the label is shown only while the copied comment remains unchanged from the original proposal;
- the first manual edit removes the source label;
- after the label disappears, the text behaves like an ordinary comment draft;
- deleting the text also removes the label;
- the original proposal and its original comment remain unchanged in history.

MVP:
- the form detects the first meaningful edit to the transferred comment;
- the source label is removed immediately after that edit;
- the label does not remain on a modified comment;
- the final action stores only the final submitted comment;
- the action remains a separate final action, not proposal acceptance.
