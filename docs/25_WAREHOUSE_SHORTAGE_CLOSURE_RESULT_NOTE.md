# 25 Warehouse — Shortage Closure Result Note

## 10.250. Required closure result for shortage

Decision: when closing a shortage entry, the user must select a closure result from a predefined list.

Closure result options:
- found;
- manually corrected;
- written off / formally removed;
- other.

Rules:
- closure result is required;
- closure cannot be completed without selected result;
- if other is selected, comment is required;
- closure actor and time are logged;
- closure result is stored in shortage history.

Purpose:
- keep shortage resolution history clear;
- support audit and later investigation;
- avoid unclear closed shortage records.

MVP approach:
- show required dropdown/select on close action;
- require comment only for other;
- save closure result, comment, actor, and timestamp.
