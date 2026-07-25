# 25 Shortages 10.348

Decision: if several shortages have the same displayed name, the disappearance message includes additional user-visible context that identifies the affected record.

Behavior:
- the message keeps the shortage name as its primary label;
- it adds enough context to distinguish the record from shortages with the same name;
- suitable context may include the project, section, equipment category, estimate block, or another characteristic already visible to the user in the product;
- the interface should prefer the smallest useful set of context fields rather than displaying all available metadata;
- the context reflects the record that disappeared from the current list, not another shortage with the same name;
- the message remains informational and follows the persistence rules defined in decision 10.345.

Architecture binding:
- the disambiguating text is assembled in `apps/web` from the shortage list/read projection;
- the `shortages` bounded context owns the shortage identity and current state, while project and section labels may come from the corresponding read model;
- no domain command, audit record, history entry, or notification is created merely because the UI displays identifying context;
- internal identifiers are not a substitute for meaningful user-visible context unless a later decision explicitly requires them.

MVP:
- identical shortage names are distinguishable in the disappearance message;
- the message uses human-readable context already available in the interface;
- the context is concise and sufficient to identify the affected record;
- no additional server-side mutation is performed.
