# PACK.IT Development Discipline Skill

Use this skill before implementing code, refactoring, adding dependencies, choosing architecture, or modifying build/dev tooling.

## Current repo status

The repository may be docs-only or early-stage. Do not assume a framework, database, hosting model or package manager unless the docs or explicit user instruction confirms it.

## Main rule

Build PACK.IT as modular domain packages, not as a giant app with mixed UI/business logic/config/CSS.

## Architecture principle

Target shape, once code exists:

```text
packages/
  core-project
  core-sections
  core-scene
  core-stage
  core-truss
  core-led
  core-bom
  core-inventory
  core-documents
  core-admin
  core-auth
  core-sync
  ui-shell
  ui-projects
  ui-scene-editor
  ui-inventory
  ui-admin
  shared-ui
  shared-types
```

Names can change, but separation must remain.

## Code discipline

- Domain rules belong in core packages.
- UI components should not contain pricing, stock, permission or calculation truth.
- Generated documents should use the same data models as UI and warehouse.
- Avoid over-engineering, but do not collapse domains into a god module.
- Prefer native/platform features before adding dependencies.
- Add tests for business rules before UI polish.
- Keep commits focused.
- Docs are source of truth; if docs and code disagree, flag it.

## Donor app rule

Old FegCalc/QucCalc code is a donor of:

- proven business logic;
- formulas;
- reference data;
- accepted UI behavior;
- edge cases.

It is not a codebase to copy blindly.

Watch for old-app problems:

- god configs;
- mixed stage/truss/BOM logic;
- CSS `!important` arms race;
- duplicated state;
- UI-only business truth;
- static-app security assumptions.

## Dependency discipline

Before adding a dependency, ask:

1. Is this truly needed?
2. Can the platform/stdlib do it?
3. Does it increase bundle/runtime risk?
4. Does it leak domain logic into UI?
5. Is it compatible with future mobile/offline needs?

## Tooling hints

Use local tools when available:

- graphify: inspect dependency graph and coupling;
- ponytail: audit for over-engineering and unnecessary code;
- ui-ux-pro-max: UI/design-system guidance;
- cybersecurity skills: authz, PII and audit patterns.

## Red flags

- A feature works only because a component has hidden side effects.
- Business rules exist in CSS/markup.
- Same project state stored in multiple incompatible formats.
- A PDF/export has its own manual calculation logic.
- Permission checks exist only in navigation/sidebar.
- Tests cover components but not domain rules.
