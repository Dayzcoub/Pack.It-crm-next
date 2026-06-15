# 25 Warehouse — Problem Report Multi Problem Note

## 10.192. One report for multiple problems

Decision: the internal warehouse problem/loss report may include multiple problems when more than one problem should be documented together.

Rules:
- a report can be created for one problem row;
- if there are multiple related problem rows, they can be combined into one report;
- the user chooses which problem rows to include;
- each included problem keeps a link to its source row or source operation where possible;
- the report remains internal by default.

Purpose:
- avoid creating too many small documents;
- allow one clear report for a group of related warehouse problems;
- keep problem handling flexible for real workflows.

MVP approach:
- support single-problem report creation;
- support selecting multiple problem rows for one report where practical;
- show all included problems as separate rows/sections inside the report.
