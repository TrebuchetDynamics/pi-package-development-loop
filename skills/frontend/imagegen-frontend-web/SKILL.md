---
name: imagegen-frontend-web
description: Use when generating section-by-section website design reference images for landing pages or marketing sites.
---

# Website UI Image Direction

Generate website design reference images for the requested page or sections. Deliver actual images when generation is available; code or a prompt alone does not satisfy an image request.

## Workflow

1. Inspect the brief, brand assets, and supplied references. Identify the audience, message hierarchy, required sections, and image count. Use the requested layout and crop when specified.
2. Define typography, palette, spacing, image treatment, and section rhythm. Give the page a clear primary action and enough readable content to judge the design; avoid invented testimonials, metrics, or certifications presented as facts.
3. Generate at a useful scale. Split a long page into section images only when needed for legibility; keep shared tokens and content consistent. A hero-only request needs a hero, not a full default site pack.
4. Inspect generated images for legible copy, hierarchy, alignment, media framing, and consistency. Correct substantive mismatches, using the supplied reference for edits when the tool supports it.
5. Deliver the requested image set. If the generation tool fails or is unavailable, report that precisely; a written prompt can be offered as a labeled fallback.

## Conditional references

- [Composition](references/composition.md): layout variation, hero direction, and section planning.
- [Visual language](references/visual-language.md): typography, component rhythm, colors, materials, and media direction.
- [Page quality](references/page-quality.md): multi-image consistency, page packs, and final review.

User constraints override reference defaults. Image generation follows the available host tool's input, editing, cost, and output rules. Avoid open-ended regeneration loops; stop after satisfying the brief or when a concrete limitation requires new input.

## Output contract

Return images with brief labels for their section/viewport and disclose unresolved issues. Example: a request for a light editorial hero remains a light editorial hero, even when a catalog suggests a dark, multi-section composition.

## Shared contract

Follow [the shared skill contract](../../shared/COMMON-CONTRACT.md) for scope, authorization, available tools, and verification evidence.
