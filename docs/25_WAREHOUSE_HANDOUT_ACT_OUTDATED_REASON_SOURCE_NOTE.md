# 25 Warehouse — Handout Act Outdated Reason Source Note

## 10.167. Source of outdated reason

Decision: the reason why a handout act version became outdated can be both automatic and manual.

Rules:
- the system may suggest a reason from detected changes;
- the user may enter the reason manually;
- the user may edit or replace the suggested reason;
- the final reason is stored in the document history;
- the reason is shown for outdated versions.

Examples of automatic suggestions:
- items changed;
- pickup person changed;
- document regenerated after handout correction;
- view mode changed.

Purpose:
- save time when the system can explain the change;
- still allow a human-readable explanation when automatic text is not enough;
- make document history understandable.

MVP approach:
- support optional auto-suggested reason;
- support manual reason field;
- store the final reason with the outdated handout act version.
