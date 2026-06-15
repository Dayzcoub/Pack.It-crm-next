# 25 Warehouse — Handout Act View Mode Note

## 10.158. Handout act table view mode

Decision: the handout act should support both display modes: one common table and grouped by categories.

Rules:
- the act can show all items in one common table;
- the act can also group items by categories or directions;
- the user should be able to choose the view mode when generating the document, or the company may set a default mode in settings;
- category grouping may follow the same category structure as the picking list.

Examples of groups:
- sound;
- light;
- LED;
- stage;
- truss;
- cables;
- power;
- cases / containers.

Purpose:
- one common table is simpler for small projects;
- grouped view is more readable for large projects;
- different teams can use the document in the format that fits their process.

MVP approach:
- support common table mode;
- support grouped-by-category mode;
- allow choosing mode during PDF/print generation or through a warehouse document setting.
