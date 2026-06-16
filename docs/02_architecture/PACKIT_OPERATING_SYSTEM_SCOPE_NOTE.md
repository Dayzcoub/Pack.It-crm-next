# PACK.IT operating system scope note

Date: 2026-06-16

Decision: PACK.IT is not only a 3D constructor with CRM support. PACK.IT must be treated as a full operating system / combined work platform for an event rental and production company.

Core scope:

- rental company management;
- projects and clients;
- quotes, documents and finance flow;
- warehouse, inventory, movements, labeling, scanning and stock control;
- equipment availability, shortages, substitutions and subrent;
- team assignment and project task distribution;
- worker-to-worker communication;
- project chats and operational communication;
- field communication scenarios, including future intercom / onsite comms control;
- mobile field workflows for technicians, warehouse and project crew;
- 3D Project Scene First constructor as one of the main entry points into the workflow;
- BOM, price, PDF and technical package generation from the project model;
- access roles and visibility rules for office, warehouse and field staff.

Strategic correction:

PACK.IT should not be positioned as a narrow alternative to Stage Lab or as only a visual layer above CRM. It must be positioned as a full company workbench: the system where the whole rental/production company plans, assembles, communicates, executes, tracks and closes projects.

3D is still strategically important, but it is not the whole product. The product center is the unified Project/Company operating model:

```text
Company / Workspace
  -> Clients / Projects / Finance / Documents
  -> Warehouse / Assets / Inventory / Scanning
  -> Project Scene / 3D Constructor / BOM
  -> Team / Tasks / Field execution
  -> Chats / Notifications / Field comms
  -> Reports / Analytics / History
```

Implication for architecture:

PACK.IT modules must be designed as parts of one connected operational platform, not as isolated calculators or isolated CRM screens. The ProjectModel and WorkspaceModel must connect visual construction, warehouse, people, tasks, communication and documents.
