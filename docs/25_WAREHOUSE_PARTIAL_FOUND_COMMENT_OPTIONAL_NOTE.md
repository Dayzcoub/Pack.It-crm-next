# 25 Warehouse — Partial Found Comment Optional Note

## 10.258. Comment is not required for partial found shortage

Decision: when closing part of a shortage with found result, comment is not required.

Rules:
- user can enter found quantity without adding a comment;
- found quantity is restored automatically;
- remaining quantity stays open if not fully resolved;
- actor, time, found quantity, and remaining quantity are logged;
- optional comment may be supported, but it is not mandatory.

Purpose:
- keep simple found actions fast;
- avoid slowing warehouse keeper work;
- still preserve enough audit data through quantity, actor, and timestamp.

MVP approach:
- found quantity field is required;
- comment field is optional;
- system logs quantity and action metadata.
