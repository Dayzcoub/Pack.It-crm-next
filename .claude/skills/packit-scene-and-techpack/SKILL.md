# PACK.IT Scene, 3D Constructor and Tech Pack Skill

Use this skill before implementing SceneModel, stage/truss/LED constructors, 2D/3D viewers, BOM extraction, client preview, working drawings, PDF tech packs, or asset library.

## Main rule

3D is a powerful project entry point, but it must not be disconnected artwork. Scene data must generate or reconcile with BOM, quote, warehouse reservations, documents and tasks.

## SceneModel principles

```text
SceneModel
  -> venue/stage coordinate system
  -> objects with real dimensions, positions, rotations
  -> catalog links and metadata
  -> connection points / rigging points where relevant
  -> generated BOM lines
  -> drawing views and annotations
```

Every scene object should know whether it is:

- a visual-only helper;
- a billable catalog item;
- a warehouse-reserved item;
- a structural/rigging object;
- a document annotation;
- a client-preview-only decorative object.

## Asset Library

Assets must be real-scale and metadata-rich:

- dimensions;
- weight;
- category;
- catalog/SKU/warehouse link;
- connection points;
- default price/rental unit;
- preview thumbnail;
- optional GLB/LOD files;
- manufacturer/model data;
- safety/load notes where relevant.

Blender can be used as an asset/render pipeline, not as the live web constructor core.

Recommended approach:

```text
ProjectModel / SceneModel
  -> WebGL editor/viewer (Three.js/Babylon/React Three Fiber or chosen stack)
  -> optional Blender worker for renders, previews, asset conversion, GLB cleanup
  -> PDF / Tech Pack / Client Preview
```

## Technical drawing target

Use WYSIWYG-like working drawings as output orientation:

- isometric overview;
- top plan;
- front/elevation views;
- stage/zone sheets;
- fixture symbols and legend;
- equipment list on sheet;
- fixture IDs;
- DMX/universe/patch/address data where relevant;
- truss/stage/LED layout;
- rigging/hang/support points;
- cable/power/data lines where relevant;
- title block with event/date/venue/version/author/sheet number;
- A2/A3/PDF export.

The drawing must be generated from project data, not redrawn manually as separate truth.

## Client Preview target

Use Axys Vision-like immersive preview as presentation orientation:

- protected/public client link;
- no internal prices/stock data;
- 3D preview with camera presets;
- day/night modes;
- optional light animation and LED placeholders;
- project version comparison;
- pinned client comments;
- approval action/status;
- export selected preview views into quote/PDF.

## Constructor domain rules

Known accepted baselines and rules from old/quick app are donor knowledge, not code to copy. Reuse formulas and behavior, not architecture.

- Stage, Truss and LED must remain separate core domains.
- Quick constructors can use ideal catalog logic.
- CRM/estimate flow must use warehouse availability and reservation logic.
- PDF output should be projection from structured data.

## Red flags

- Pretty 3D scene with no BOM traceability.
- BOM generated from manual lists while scene shows something else.
- Client preview not matching quote/warehouse.
- Drawing annotations stored only as pixels/screenshots.
- 3D constructor code mixed directly with pricing, warehouse and CSS hacks.
