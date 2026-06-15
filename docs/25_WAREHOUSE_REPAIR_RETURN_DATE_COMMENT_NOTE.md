# 25 Warehouse — Repair Return Date and Comment Note

## 10.214. Repair return date requirement

Decision: a planned repair return date is not required for MVP. A repair comment is enough.

Rules:
- do not require planned return date when moving an item to in_repair;
- allow a free comment for repair details;
- the comment can include expected return timing, repair reason, contractor notes, or any other useful context;
- in_repair remains unavailable for booking/reservation;
- the status transition must still be logged with user, date, time, and repair destination.

Purpose:
- keep the repair workflow simple for small teams;
- avoid forcing inaccurate dates;
- still allow practical notes when repair details are known.

MVP approach:
- required: repair destination type;
- optional: repair comment;
- not required: planned return date.
