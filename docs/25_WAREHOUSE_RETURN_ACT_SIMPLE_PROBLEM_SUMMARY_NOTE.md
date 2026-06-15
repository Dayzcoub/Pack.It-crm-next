# 25 Warehouse — Return Act Simple Problem Summary Note

## 10.174. Return act item status detail

Decision: the return act does not need per-item statuses like fully accepted or partially accepted. A general problem row/block is enough when something does not match.

Rules:
- do not add detailed accepted status to every return row by default;
- normal returned items stay in the common return list;
- if something is wrong or incomplete, it is shown in the problem block;
- the problem block is only shown when problem rows exist.

Purpose:
- keep the return act readable;
- avoid overloading the document with unnecessary statuses;
- make exceptions visible without complicating every line.

MVP approach:
- use a simple return item table;
- use a conditional problem block for mismatches and exceptions;
- keep detailed handling in the warehouse problem flow.
