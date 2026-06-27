# PACK.IT reference note: CAST WYSIWYG / working drawing output

Date: 2026-06-16

Reference: professional stage/light design drawings similar to CAST WYSIWYG Design/Perform working drawings.

Important: WYSIWYG is not the product model for PACK.IT as a whole. It is a visual/documentation reference for the quality and structure of technical drawing output.

## What to use as an orientation

PACK.IT should be able to produce project documentation that feels close to professional WYSIWYG working drawings:

- general 3D/isometric stage view;
- top plan view;
- front/elevation views;
- separate stage/zone sheets;
- fixture symbols and legend;
- equipment list on the sheet;
- fixture numbering;
- DMX/universe/patch/address data where relevant;
- truss, stage, LED and screen layout;
- rigging and hang positions;
- cable/power/data lines where relevant;
- project title block with event, date, venue, version, author, sheet number and notes;
- A2/A3 style export for PDF technical packs.

## PACK.IT difference

PACK.IT must not be only a drawing tool. The drawing must be generated from the same operational ProjectModel that drives:

- warehouse availability;
- BOM and equipment lists;
- pricing and quotes;
- shortages and substitutions;
- subrent;
- crew tasks;
- project communication;
- loading, checkout and return;
- field execution and checklists.

In other words:

```text
WYSIWYG-like output = professional technical drawing reference
PACK.IT = operating system that generates drawings from live project/workspace data
```

## Product implication

The target output for PACK.IT Tech Pack should include at least:

1. Overview sheet
   - isometric view;
   - title block;
   - compact equipment summary.

2. Stage plan sheet
   - top view;
   - stage dimensions;
   - truss, LED, audio, light positions.

3. Light plot sheet
   - fixtures;
   - fixture IDs;
   - DMX/universe/addresses;
   - symbols and legend.

4. Rigging/truss sheet
   - truss segments/nodes;
   - supports/bases/points;
   - loads or load warnings where available.

5. Warehouse/BOM sheet
   - equipment grouped by category;
   - quantities;
   - stock status;
   - shortages/subrent.

6. Field execution sheet
   - crew tasks;
   - zones;
   - checklists;
   - contact/communication references.

## Architecture implication

The drawing layer should be generated from structured project data, not manually drawn as a separate artifact.

```text
ProjectModel / SceneModel
  -> 3D/2D viewer
  -> drawing layout engine
  -> PDF tech pack
  -> warehouse/BOM/tasks/docs
```

This prevents the drawing, estimate, stock status and field tasks from becoming inconsistent.
