# 25 Shortages 10.335

Decision: after a shortage-resolution conflict, the read-only recovery view shows only user-entered text fields that may be useful to copy into a new action.

Behavior:
- show the final mandatory reason or explanation text, if that field contained user-visible text;
- show the general comment, if it contained text;
- do not show the selected result type, quantities, dates, identifiers, calculated values, or other non-text fields from the obsolete action;
- keep each preserved text field separately labelled so the user understands its original purpose;
- text remains selectable and copyable manually;
- no "Copy all" action is provided;
- closing and deleting the recovery view follows decisions 10.332 and 10.333.

Architecture binding:
- the recovery view and its retained text are transient `apps/web` session state;
- retained text is not written to `shortages` domain history, `audit`, or any server-side draft store;
- the current shortage state shown behind or beside the recovery view is read from the authoritative `shortages` projection;
- starting a new resolution creates a new `shortages.resolve` command and does not reuse the conflicting command automatically.

MVP:
- only non-empty user-facing text fields are displayed;
- obsolete structured values cannot be mistaken for the current shortage state;
- each text field can be selected and copied manually;
- no retained recovery data survives the current page session or explicit confirmed deletion.
