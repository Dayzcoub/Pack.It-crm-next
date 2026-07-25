# 25 Shortages 10.355

Decision: when both the project and section names are long, the available width is divided equally between them.

Behavior:
- the project and section receive equal display space within the context line;
- neither value has visual priority over the other;
- each value is truncated independently with an ellipsis when it exceeds its allocated width;
- the explicit labels and separator remain visible: `Проект: … | Раздел: …`;
- the full value of each truncated field remains available on hover and keyboard focus according to decision 10.354;
- the fallback value `Не указан` follows the same layout rules.

Architecture binding:
- width allocation, truncation, hover, and focus behavior belong to `apps/web` presentation logic;
- the UI uses the project and section values from the authoritative shortage read projection;
- display truncation does not modify or persist source values;
- rendering this context creates no shortage history, audit event, notification, or source-domain command.

MVP:
- project and section share the available context-line width equally;
- both values can be truncated independently;
- complete values remain accessible without changing the underlying data;
- the layout remains readable for pointer and keyboard users.
