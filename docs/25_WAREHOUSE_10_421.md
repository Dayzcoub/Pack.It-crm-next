# 25 Shortages 10.421

Decision: shortage proposal history preserves the author's display-name snapshot from the time of the action, even if the author's user account is later deleted.

Behavior:
- proposal and shortage history entries keep the user-facing author name that was shown when the relevant action occurred;
- deleting the underlying user account does not replace historical author names with a generic `Удалённый пользователь` label;
- historical records remain readable and attributable without requiring the original account to continue to exist;
- the preserved name is historical display data and does not reactivate, restore, or otherwise recreate the deleted account;
- current permissions and account state are still resolved from the current identity/access model, not from the historical snapshot.

Architecture binding:
- `shortages` owns proposal and shortage-domain history and stores the author display snapshot required for that history;
- identity/account deletion must not break referential readability of existing shortage history;
- `audit` independently records significant account/permission changes according to the system audit rules;
- history rendering must not require a live user lookup in order to show the historical author name.

MVP:
- old shortage proposals continue to show the author's historical display name after account deletion;
- no generic replacement label is used solely because the account no longer exists.
