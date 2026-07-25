# 25 Shortages 10.349

Decision: when additional context is needed to distinguish shortage records with the same name, the message always shows the same context set: project and section.

Behavior:
- the disappeared shortage is identified by its displayed name;
- the message additionally shows the related project and section;
- the same context structure is used even when one of the two attributes alone would be sufficient for distinction;
- context order and labels remain consistent across messages;
- internal identifiers are not exposed as a substitute for user-facing project and section names.

Architecture binding:
- the message is built in `apps/web` from the authoritative current shortage projection and the previously displayed record context;
- project and section values are read-only display data and do not change the shortage state;
- rendering the message does not invoke `shortages.resolve`, `shortages.accept_proposal`, or another source-domain command;
- it creates no shortage history, audit event, side effect, or notification.

MVP:
- duplicate shortage names are disambiguated with both project and section;
- the context format is uniform for all such messages;
- only user-facing names already available to the list projection are displayed;
- the message remains informational and follows the lifetime rules defined for the list-level notice.
