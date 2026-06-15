# 25 Warehouse — Inventory Report No Attachment Thumbnails Note

## 10.186. Attachment thumbnails in inventory report

Decision: the inventory report should not show photos or files as small thumbnails for discrepancy rows.

Rules:
- do not render image thumbnails in the inventory report by default;
- keep the report compact and text-focused;
- if attachments exist in the system, they can remain available in the related inventory/discrepancy record;
- the generated report does not need to embed them.

Purpose:
- keep the inventory report short and readable;
- avoid turning the report into a heavy photo document;
- keep attachment review inside the system interface where needed.

MVP approach:
- show discrepancies grouped by category;
- show concise row details;
- do not include thumbnail previews in the generated inventory report.
