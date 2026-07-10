# PACK.IT reference note: Axys Vision / immersive client preview

Date: 2026-06-16

Reference: Axys Vision (`axysvision`, `axysvision.com.br`) appears to be a studio/service focused on immersive project visualization and event previz, not a rental CRM, manufacturer, or public SaaS constructor.

Observed positioning from Instagram profile/screens:

- `Especialista em experiências imersivas` — specialist in immersive experiences;
- `Faça seu cliente viver o projeto antes da execução` — let the client experience the project before execution;
- categories: events, stands, real estate, churches;
- video frames show 3D modelling, rendered venue/stage preview, lighting/console-like control interfaces and client-facing visual walkthroughs.

## Interpretation

Axys Vision should be treated as a reference for client-facing immersive preview and visual pre-sale experience.

It is not currently a confirmed reference for:

- full rental company CRM;
- warehouse management;
- task management;
- public online constructor;
- automatic BOM/quote generation;
- operating system for production workflow.

It is a reference for this product idea:

```text
Before the event is built, the client can already see and feel it.
```

## PACK.IT opportunity

PACK.IT should include, in the roadmap, a `Client Preview` / `Client Vision` mode generated from the live ProjectModel and SceneModel.

Possible feature set:

- public or protected client link;
- project preview without internal prices, warehouse data and operational details;
- 3D venue/stage/LED/light preview;
- camera presets: audience view, top view, front view, operator view;
- day/night mode;
- optional animated light scene preview;
- LED content preview/placeholders;
- compare project versions/options;
- client comments pinned to zones or objects;
- approval button / approval status;
- export selected preview views to PDF quote or tech pack.

## Strategic difference

```text
Axys Vision:
manual immersive 3D/previz service for selling and explaining a project

PACK.IT:
automatic immersive client preview generated from the same live project data
that also drives warehouse, quote, BOM, tasks, crew, communication and documents
```

PACK.IT should not copy Axys Vision as a business model, but should absorb the core user value:

```text
The client understands and approves the event before execution.
```

## Architecture implication

Client Preview must not be a separate manual scene disconnected from the operational project. It should be a presentation layer over the same data model:

```text
ProjectModel / SceneModel
  -> internal 3D constructor
  -> BOM / warehouse / quote / tasks
  -> tech pack drawings
  -> client preview link
```

This avoids the common production problem where a beautiful client render, the warehouse list, the quote and the field task plan describe different versions of the same project.
