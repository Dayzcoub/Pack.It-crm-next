# 25 Warehouse — Bulk No Overplan Note

## 10.243. Bulk quantity cannot exceed planned quantity

Decision: for bulk items, the confirmed quantity cannot be greater than the planned/required quantity in the current document.

Rules:
- user may confirm exactly the required quantity;
- user may confirm less than the required quantity;
- user cannot confirm more than the required quantity;
- if less is confirmed, the row remains under-confirmed and requires follow-up review;
- any extra items are handled outside the current document workflow;
- if extra items are real company stock, quantity is adjusted manually in the relevant item/nomenclature record after separate review.

Purpose:
- avoid stock mix-ups;
- prevent items from other projects, locations, or third parties from entering the document accidentally;
- keep handout/return documents tied to planned quantities.

MVP approach:
- quantity input max value equals required quantity;
- plus button cannot go above required quantity;
- direct input above required quantity is rejected or clamped with a warning;
- separate manual stock adjustment handles real extra quantity after review.
