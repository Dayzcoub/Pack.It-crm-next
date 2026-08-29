# 25 Shortages 10.429

Decision: the time-based priority between active shortage-resolution proposals is strict.

Behavior:
- for one shortage, active proposals from different authors are ordered by proposal creation time, oldest first;
- while an earlier proposal remains active and reviewable, a later proposal cannot be accepted ahead of it;
- warehouse users may inspect later proposals, but acceptance of a later proposal is blocked by the earlier active proposal;
- the priority is based on the original proposal creation time, not on later edits or reconfirmations;
- editing or reconfirming an existing proposal does not move it to the end of the queue;
- when the earlier proposal leaves the active/reviewable set because it is accepted, withdrawn, automatically closed, or otherwise becomes inapplicable under established shortage rules, the next active proposal becomes first in priority.

Architecture binding:
- `shortages` owns proposal ordering and validates strict priority in the acceptance use case;
- acceptance must check the latest proposal states and queue order transactionally rather than relying only on UI ordering;
- stale attempts to accept a later proposal after queue state changes follow the existing conflict/reconciliation rules;
- proposal history retains original creation time independently from edit history.

MVP:
- active proposals are shown and processed oldest first;
- a later proposal cannot be accepted while an earlier applicable proposal remains active;
- edits do not reset proposal priority.
