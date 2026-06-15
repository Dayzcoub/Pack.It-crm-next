# 25 Warehouse — Documents Summary Note

## 10.204. Warehouse documents summary

Decision: collect the current warehouse document decisions into one summary document before moving to the next warehouse workflow block.

## 1. Picking list

Purpose: internal warehouse document for preparing equipment for a project.

Rules:
- internal only;
- no prices;
- can be generated as one common project list and separately by equipment categories;
- category split is automatic, based on project/equipment data;
- default mode is simplified, without detailed storage locations;
- extended storage location mode can later be enabled by admin;
- supports both interactive workflow and PDF/print;
- supports partial picking;
- partial remaining quantity can be marked as dobor / next trip with comments.

## 2. Transfer block between projects

Purpose: handle equipment moving directly from one project/site to another.

Rules:
- transfer is not ordinary dobor;
- no separate transfer PDF is required for MVP;
- transfer is shown as a block inside the picking list;
- visible in both related projects;
- has responsible person;
- statuses: planned, departed, delivered;
- status changes can be made by assigned responsible person or project manager;
- related people receive notifications;
- overdue/risk state is shown if timing is missed;
- visibility is limited to people related to the transfer.

## 3. Handout act

Purpose: internal document confirming equipment handout from warehouse.

Rules:
- optional, enabled in settings;
- internal only;
- generated manually by button;
- default confirmation is system-based: who issued, who received, date/time;
- signatures are optional through settings;
- detailed item condition mode is optional for larger companies;
- can be shown as one table or grouped by categories;
- cases/containers can be shown in a separate block or inside the general table;
- pickup person is recorded;
- external pickup person can be entered manually with name/organization, phone, and comment;
- generated acts are stored in history;
- regenerated acts create new versions;
- old versions are marked outdated with reason;
- outdated reason can be suggested automatically and manually edited.

## 4. Return act

Purpose: internal document confirming equipment return to warehouse.

Rules:
- uses the same settings logic as the handout act;
- optional and internal;
- generated manually where needed;
- problem rows are shown in a separate block only if they exist;
- delivery person is recorded;
- external delivery person can be entered manually with name/organization, phone, and comment;
- accepted-by warehouse user is recorded;
- no per-item full/partial status is required in the report;
- compact summary is included;
- problem attachments are shown;
- images/files are shown as small thumbnails or compact file cards;
- history/versioning follows handout act logic;
- outdated reason can be suggested automatically and manually edited.

## 5. Inventory report

Purpose: internal report for inventory count discrepancies.

Rules:
- generated manually by button when needed;
- internal only;
- no prices;
- main report shows discrepancies only;
- optional full checked-list checkpoint can be generated when needed;
- discrepancies are grouped by equipment category;
- report records who conducted the inventory;
- no attachment thumbnails in the report;
- compact summary is shown at the top;
- generated reports are stored in document history;
- no versioning and no outdated status are required;
- repeated generation creates another separate history record.

## 6. Internal problem/loss report

Purpose: internal report for warehouse problems, losses, damages, incomplete returns, stock discrepancies, and similar operational cases.

Rules:
- created manually from one or more problem rows;
- multiple related problems can be combined into one report;
- photos and files are included as small thumbnails or compact file cards;
- probable cause is filled when the problem is detected and pulled into the report;
- users with inventory access and warehouse change permissions can create the report;
- generated reports are stored in warehouse document history;
- default MVP retention guideline is last 6 months;
- report includes resolution/action field;
- report can be created before final resolution is known;
- unresolved reports use requires resolution status;
- who can close requires resolution is configurable by company admin/director;
- closing resolution can automatically update warehouse item status;
- automatic status update requires user confirmation before applying.

## Common principles

- Warehouse documents are internal by default.
- Prices are excluded by default unless explicitly required later.
- Small teams should not be forced into strict paperwork.
- Admin/director settings should enable stricter workflows for larger companies.
- Important actions must be logged with user, date, time, and source context.
- Documents should reuse general warehouse document history where practical.
