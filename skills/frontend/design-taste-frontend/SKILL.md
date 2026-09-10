---
name: design-taste-frontend
description: Anti-slop taste rules for marketing sites, landing pages, portfolios, and editorial redesigns. Use when visual distinctiveness is the main goal; not product dashboards, data tables, or multi-step application UI.
---

# Design Taste Frontend

Create a distinctive marketing page, portfolio, or editorial site from the actual brief. Preserve the existing stack, brand assets, content, and routes unless the requested redesign includes changing them. Style advice is contextual; it does not authorize dependency installation or override accessibility.

## Workflow

1. Inspect the brief, supplied references, existing tokens, and relevant page/components. State one concise design read: page kind, audience, visual direction, and constraints. Ask only if competing interpretations change the result.
2. Choose layout variance, motion intensity, and density to suit the audience. Keep `DESIGN_VARIANCE`, `MOTION_INTENSITY`, and `VISUAL_DENSITY` as consistent names when the detailed guidance needs dials. Existing design systems outrank default recipes.
3. Sketch the page's information hierarchy and section rhythm. Give the page one clear visual focus; use real content and assets. Choose a pattern because it serves the message, not because a catalog lists it.
4. Implement within the existing framework. Use semantic HTML, keyboard-operable controls, visible focus, readable contrast, responsive media, and reduced-motion behavior. Add a dependency only when the existing stack cannot reasonably supply the needed behavior.
5. Verify the relevant desktop/mobile states and interactions, then run the project's applicable checks. Distinguish browser observations from source-only review; report missing visual verification explicitly.

## Read only what the task needs

- [Brief, dials, and design-system selection](references/brief-and-system.md): ambiguous art direction or choosing a foundation for a new project.
- [Implementation guidance](references/implementation.md): typography, components, responsive behavior, motion, and dark mode; read the applicable subsection.
- [Pattern catalog](references/pattern-catalog.md): seek an alternative composition only when the current brief needs one; avoid loading the entire catalog for a small fix.
- [Redesign and verification](references/redesign-and-verification.md): preserving an existing page or checking the completed result.
- [Systems and source links](references/systems-and-sources.md): when a named design system is selected; verify current official documentation before using versioned commands.

## Output contract

Return the working artifact, the key design decision, and validation evidence. For a design-only request, return the requested concept/spec instead of implementation. A request to restyle a hero ends when that hero and its affected responsive states are verified; it does not imply a full-site rebuild.

## Shared contract

Follow [the shared skill contract](../../shared/COMMON-CONTRACT.md) for scope, authorization, available tools, and verification evidence.
