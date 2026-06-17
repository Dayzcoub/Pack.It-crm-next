# 25 Warehouse — Bulk Quantity Control Note

## 10.242. Bulk quantity controls on scanner screen

Decision: bulk quantity can be changed both with minus/plus buttons and direct numeric input.

Rules:
- show compact minus button;
- show numeric quantity field;
- show compact plus button;
- user can tap minus/plus for quick adjustment;
- user can type exact quantity manually;
- quantity changes update current scan context and progress counter.

Purpose:
- make small corrections fast;
- support exact quantity entry;
- keep scanner screen convenient on mobile.

MVP approach:
- quantity control layout: minus / input / plus;
- prefill with required quantity after bulk row scan;
- allow direct edit before final document confirmation.
