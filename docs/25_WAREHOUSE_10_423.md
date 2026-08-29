# 25 Shortages 10.423

Decision: one author may have only one active proposal for a specific shortage at a time.

Behavior:
- an author cannot create a second simultaneously active proposal for the same shortage;
- if the author needs to change the proposed resolution while keeping the same resolution type, the existing active proposal is edited according to decisions 10.403–10.407;
- if a different resolution type is required, the current proposal must be withdrawn and a new proposal created according to decision 10.406;
- withdrawn and superseded proposal history remains preserved;
- other users may still have their own active proposals for the same shortage, subject to the existing shortage/proposal rules.

Architecture binding:
- `shortages` owns the invariant of at most one active proposal per `(shortage, author)` pair;
- the invariant must be enforced transactionally when creating or reactivating a proposal;
- `shortages.propose_resolution` permits proposal creation but does not bypass this invariant;
- proposal history remains in the shortage domain history and significant actions remain independently auditable.

MVP:
- when the author already has an active proposal for the shortage, the UI does not offer creation of another active proposal;
- the user is directed to edit or withdraw the existing proposal as appropriate;
- concurrent create attempts must not result in two active proposals for the same author and shortage.
