# 25 Warehouse — Block Damaged / Not Working to Available Note

## 10.211. Blocking available status for damaged or non-working items

Decision: if a returned item has a problem category such as damaged or not working, the system must hard-block moving it to available until the problem is resolved.

Rules:
- damaged items cannot be moved to available while the blocking problem is open;
- non-working items cannot be moved to available while the blocking problem is open;
- user warning is not enough for these blocking categories;
- the problem must be resolved first or the item must be moved to another appropriate status such as in repair, quarantine, written off, or another configured non-available status;
- any attempted blocked transition should show a clear explanation.

Purpose:
- prevent unsafe or unusable equipment from being booked again;
- protect project quality and warehouse reliability;
- keep availability logic strict for critical problem categories.

MVP approach:
- mark damage and not-working problem categories as availability blockers;
- block returned -> available until resolution/status update;
- allow non-blocking problem types, such as completeness issues, to follow the receiver decision flow from the previous note.
