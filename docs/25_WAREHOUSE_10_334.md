# 25 Shortages 10.334

Decision: the read-only recovery view shown after a shortage-resolution conflict does not provide a separate “Copy all” action.

Behavior:
- the user copies only the specific text or values they need;
- all displayed values remain selectable in the read-only view;
- the interface does not assemble the attempted action into a combined clipboard payload;
- closing the recovery view still follows the confirmation rule from decision 10.333;
- the actual current shortage state remains separate from the preserved attempted-action data.

Architecture binding:
- text selection and clipboard interaction are transient `apps/web` behavior;
- the recovery view does not persist an additional copyable document or payload;
- copying data creates no `shortages` domain-history or `audit` event;
- no additional backend permission is introduced;
- the conflicting attempted action remains unapplied and does not invoke `shortages.resolve` again.

MVP:
- there is no “Copy all” button;
- individual displayed values can be selected and copied manually;
- manual copying does not change or dismiss the recovery view;
- copied data is not tracked by the application;
- closing the view still requires explicit confirmation before the temporary data is deleted.
