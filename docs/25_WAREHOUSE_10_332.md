# 25 Shortages 10.332

Decision: after a conflict closes the editable resolution form, its entered data remains available in a separate read-only view until the user explicitly closes that view, but only within the current page session.

Behavior:
- the read-only view remains accessible while the current page session is alive;
- navigating within the supported shortage screen does not remove the view unless the user explicitly closes it;
- the user can select and copy displayed text and values but cannot edit or submit them;
- reloading the page, closing the tab, or otherwise ending the page session permanently removes the retained draft data;
- this temporary view does not restore the obsolete action and does not imply that it can still be submitted;
- the current shortage state remains authoritative and is shown separately from the retained conflicting draft.

Architecture binding:
- retention and presentation of the conflicting draft are transient `apps/web` session state;
- the retained values are not persisted in `shortages`, `audit`, browser durable storage, or any server-side draft store;
- the conflicting draft does not create a domain event and is never included in a later `shortages.resolve` command automatically;
- any new resolution starts from the current shortage state and requires a new valid command with `shortages.resolve`.

MVP:
- the read-only draft remains available until explicitly closed during the current page session;
- the draft disappears after reload, tab close, or another page-session reset;
- all retained fields can be copied but not edited or submitted;
- no temporary draft data is persisted to the server or durable browser storage;
- the obsolete draft and the current shortage state are visually distinguishable.
