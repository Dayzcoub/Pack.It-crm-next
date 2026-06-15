# 25 Warehouse — Return Act Problem Block Note

## 10.170. Problem block in the return act

Decision: the return act should show problem rows as a separate block when such rows exist.

Rules:
- if the return has problem rows, show them in a separate block;
- if there are no problem rows, do not show an empty problem block;
- the problem block is part of the internal return act;
- it does not automatically close or resolve the problem rows.

Examples of problem rows:
- not returned;
- incomplete return;
- requires check;
- disputed state;
- lost or missing item case.

Purpose:
- make return exceptions visible in the document;
- keep a clean act when everything is returned normally;
- connect the return act with later internal problem handling.

MVP approach:
- add conditional problem block to the return act;
- show only existing problem rows;
- keep detailed problem resolution in the separate warehouse problem flow.
