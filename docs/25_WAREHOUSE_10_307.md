# 25 Warehouse 10.307

Decision: when the confirmer leaves the `Accept proposal` flow through `Choose another result`, the assigned user's proposal comment is transferred into the normal shortage action form as an editable draft.

Behavior:
- the proposal comment is copied into the normal action form;
- the confirmer may edit or delete the transferred text before saving;
- the transferred text is not saved automatically and has no effect until the normal action is submitted;
- no other proposal values are transferred automatically unless defined separately;
- if the proposal has no comment, the normal action comment field opens empty.

MVP:
- transfer applies only to the proposal comment;
- the copied comment behaves like ordinary unsaved form text;
- cancelling the normal action does not modify the original proposal;
- the original proposal and its original comment remain unchanged in history;
- the final result is logged as a separate action, not as proposal acceptance.
