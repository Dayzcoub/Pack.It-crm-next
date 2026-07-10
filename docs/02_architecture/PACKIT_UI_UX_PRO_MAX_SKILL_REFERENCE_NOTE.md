# PACK.IT reference note: UI/UX Pro Max skill

Date: 2026-07-10

Reference: `nextlevelbuilder/ui-ux-pro-max-skill`

Repository: `https://github.com/nextlevelbuilder/ui-ux-pro-max-skill`

Purpose: external UI/UX design intelligence skill for AI coding agents. Use it as a design-quality layer for PACK.IT user-facing work, not as a replacement for PACK.IT domain rules.

## What it is

UI/UX Pro Max is an AI skill that provides design intelligence for building professional UI/UX across multiple platforms and frameworks.

Current metadata from `skill.json` identifies it as:

- name: `ui-ux-pro-max`;
- display name: `UI/UX Pro Max`;
- version observed: `2.6.2`;
- license: MIT;
- repository: `nextlevelbuilder/ui-ux-pro-max-skill`;
- install command template: `npx ui-ux-pro-max-cli init --ai {{platform}}`;
- supported platforms include Claude, Cursor, Windsurf, Copilot, Kiro, Roo Code, KiloCode, Codex, Qoder, Gemini, Trae, OpenCode, Continue, CodeBuddy, Droid, Warp, Augment, Antigravity and OpenClaw.

## What it contains

The project describes itself as UI/UX intelligence with:

- UI styles;
- color palettes;
- font pairings;
- product type reasoning rules;
- UX guidelines;
- chart recommendations;
- stack-specific guidelines;
- design system generation.

The README describes v2 design system generation as a multi-domain search + reasoning flow:

```text
user request
  -> product type matching
  -> style recommendations
  -> color palette selection
  -> landing page patterns
  -> typography pairing
  -> reasoning engine
  -> complete design system output
```

The generated output can include:

- recommended pattern;
- style;
- colors;
- typography;
- key effects;
- anti-patterns to avoid;
- pre-delivery checklist.

## When to apply it

The included Claude skill says it should be used when a task involves UI structure, visual design decisions, interaction patterns or UX quality control.

Must-use situations include:

- designing new pages;
- creating or refactoring UI components;
- choosing colors, typography, spacing or layout systems;
- reviewing UI code for UX, accessibility or visual consistency;
- implementing navigation, animations or responsive behavior;
- making product-level design decisions;
- improving perceived quality, clarity or usability.

Skip it for:

- pure backend logic;
- API/database-only work;
- infrastructure or DevOps;
- non-visual scripts;
- performance work unrelated to interface.

Decision criterion:

```text
If the task changes how a feature looks, feels, moves, or is interacted with,
UI/UX Pro Max should be used.
```

## Priority checks useful for PACK.IT

The skill ranks UI rule categories by priority. PACK.IT agents should especially enforce:

1. Accessibility
   - contrast;
   - focus states;
   - alt text;
   - aria labels;
   - keyboard navigation;
   - reduced motion.

2. Touch and interaction
   - 44/48px touch targets;
   - spacing between tap targets;
   - no hover-only actions;
   - loading states;
   - clear error feedback.

3. Performance
   - optimized images;
   - lazy loading;
   - reserved space to avoid layout shift.

4. Style selection
   - match product type;
   - consistent style;
   - SVG icons instead of emoji-as-icons.

5. Layout and responsive behavior
   - mobile-first breakpoints;
   - no horizontal scroll;
   - no fixed-width traps;
   - no disabled zoom.

6. Typography and color
   - semantic tokens;
   - readable base sizes;
   - adequate line height;
   - avoid raw hex values inside components.

7. Animation
   - 150–300ms meaningful motion;
   - respect reduced motion;
   - avoid decorative-only or layout-thrashing animation.

8. Forms and feedback
   - visible labels;
   - errors near fields;
   - helper text;
   - progressive disclosure.

9. Navigation patterns
   - predictable back behavior;
   - deep linking where useful;
   - avoid overloaded navigation.

10. Charts and data
   - legends/tooltips;
   - accessible colors;
   - do not rely on color alone.

## Installation notes

Claude Marketplace install:

```text
/plugin marketplace add nextlevelbuilder/ui-ux-pro-max-skill
/plugin install ui-ux-pro-max@ui-ux-pro-max-skill
```

CLI install:

```bash
npm install -g ui-ux-pro-max-cli
uipro init --ai claude
uipro init --ai codex
uipro init --ai all
```

The README says the npm package is `ui-ux-pro-max-cli`, and that older `uipro-cli` releases are stale and should not be used for current assets.

Python 3.x is required for the search/design-system scripts.

## Advanced design system command

The README documents direct search commands such as:

```bash
python3 .claude/skills/ui-ux-pro-max/scripts/search.py "SaaS dashboard" --design-system --persist -p "MyApp"
```

This can persist a design system into:

```text
design-system/
  MASTER.md
  pages/
    dashboard.md
```

The intended hierarchy:

- `design-system/MASTER.md` = global source of truth;
- `design-system/pages/<page>.md` = page-specific override;
- page override wins only for explicit deviations.

## PACK.IT application

For PACK.IT, UI/UX Pro Max should be treated as a quality gate for:

- desktop CRM/planning surfaces;
- dense project dashboards;
- warehouse screens;
- mobile field workflows;
- scanner flows;
- role-specific pages;
- 3D/scene editor UI;
- client preview;
- tech-pack/PDF presentation surfaces;
- design token decisions;
- responsive behavior.

It must not override PACK.IT domain truth. Domain behavior still comes from:

- `AGENTS.md`;
- `CLAUDE.md`;
- `.claude/skills/packit-*/SKILL.md`;
- `docs/**` domain notes.

## PACK.IT design-system implication

When UI coding begins, consider using UI/UX Pro Max to generate a PACK.IT design system, then curate it manually rather than accepting generic output blindly.

Suggested target for PACK.IT:

```text
design-system/MASTER.md
  -> tokens: colors, typography, spacing, radii, density, motion
  -> components: buttons, tables, cards, modals, forms, nav, status badges
  -> roles: manager, warehouse, tech, tech director, client/guest
  -> surfaces: desktop planning, mobile field, client preview, tech pack

design-system/pages/
  projects.md
  warehouse.md
  mobile-field.md
  scene-editor.md
  client-preview.md
  tech-pack.md
```

## PACK.IT guardrails

Agents must not let UI/UX Pro Max produce visually impressive but operationally wrong screens.

For PACK.IT, a good UI is one that makes operational state clear:

- project status;
- quote version;
- deficit/subrent;
- warehouse reservation;
- responsibility;
- field task state;
- client-visible vs internal data;
- audit-sensitive actions.

Avoid:

- generic SaaS dashboards with no event-production workflow;
- fancy UI that hides deficits or warehouse conflicts;
- desktop tables squeezed onto mobile;
- client previews exposing internal prices/warehouse/margins;
- UI components that own business truth;
- raw style decisions outside shared tokens.
