---
name: image-to-code
description: Use when turning visual website references into code, especially image-first frontend implementation workflows.
---

# Image to Code

Turn a supplied website screenshot or approved visual reference into working frontend code. The user's reference is the source of truth. Generating replacement images is optional and appropriate only when the user requests new art direction or a missing asset requires it; do not replace an attached design with a new concept.

## Workflow

1. Inspect every supplied target image and identify the requested page/section scope. Read the existing framework, assets, typography, components, and routes. Preserve functionality and the user's chosen stack.
2. Extract layout regions, spacing relationships, type hierarchy, colors, media bounds, and interaction cues. Separate measurable details from assumptions. Use relative proportions when an image does not reveal exact CSS values.
3. Plan responsive behavior from the reference. A desktop screenshot does not establish mobile behavior; make a reasonable adaptation and name important assumptions.
4. Implement real semantic UI with reusable existing components and project tokens. Use provided assets where available. Keep text selectable and controls functional; a screenshot pasted as the whole page is not a coded implementation.
5. Compare the rendered result against the reference at the matching viewport and a narrow viewport. Fix the largest hierarchy, spacing, typography, and asset discrepancies first. Run applicable build/tests and check keyboard focus, overflow, and relevant interaction states.

## Conditional references

- [Reference workflow](references/reference-workflow.md): only for planning or generating new references. The supplied-reference path above takes precedence over the upstream generation-first defaults.
- [Art direction](references/art-direction.md): for user-requested creative expansion or missing visual details; preserve established design decisions.
- [Implementation fidelity](references/implementation-fidelity.md): for extracting tokens, media framing, consistency, and comparing code with images.

Use available image tools only when needed and authorized. If a required image cannot be inspected, identify it and continue any independent setup; do not claim pixel fidelity from filenames or descriptions.

## Output contract

Return implemented paths, reference/viewport used for comparison, checks run, and remaining discrepancies. Example: a supplied pricing screenshot yields a working pricing section plus responsive adaptation, not a newly generated landing-page concept.

## Shared contract

Follow [the shared skill contract](../../shared/COMMON-CONTRACT.md) for scope, authorization, available tools, and verification evidence.
