# 25 Warehouse 10.310

Decision: after the transferred comment has been edited once, the `Transferred from assigned user's proposal` label does not return, even if the confirmer later restores the text to exactly match the original proposal comment.

Behavior:
- the label is available only before the first manual edit;
- the first meaningful edit permanently removes the label for the current form session;
- restoring the original text does not recreate the label;
- the restored text behaves like an ordinary comment draft;
- the original proposal and its original comment remain unchanged in history.

MVP:
- the form tracks whether the transferred comment has ever been edited;
- after the first edit, source-label visibility no longer depends on text equality;
- undoing or manually restoring the original text does not restore the label;
- the final action stores only the final submitted comment;
- the action remains a separate final action, not proposal acceptance.
