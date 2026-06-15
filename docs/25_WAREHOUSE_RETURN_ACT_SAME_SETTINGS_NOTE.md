# 25 Warehouse — Return Act Same Settings Note

## 10.169. Return act uses the same settings approach as handout act

Decision: the warehouse return act should use the same settings approach as the handout act.

Rules:
- the return act is enabled through warehouse settings;
- it is not mandatory for every return by default;
- it is an internal warehouse document;
- generation can be manual by button;
- system confirmation is enough by default;
- optional signatures may be supported through settings;
- simple and stricter modes can be configured later;
- generated return acts should follow the same document history/versioning logic as handout acts where applicable.

Purpose:
- keep warehouse documents consistent;
- avoid forcing paperwork on small teams;
- support stricter document flow for larger companies;
- reduce duplicate logic between handout and return documents.

MVP approach:
- reuse the same document setting pattern;
- return act default can be off / optional;
- if enabled, allow generating internal PDF/print from the return operation;
- no prices by default.
