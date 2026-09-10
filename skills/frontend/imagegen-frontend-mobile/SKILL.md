---
name: imagegen-frontend-mobile
description: Use when generating premium mobile app screen concepts, flows, or app-native UI reference images.
---

# Mobile UI Image Direction

Generate the requested mobile screen concepts or flow images. This skill produces images, not application code. Preserve the requested platform, screen count, brand, and supplied references; infer only details that do not change product intent.

## Workflow

1. Read the brief and inspect supplied images. Identify the platform, audience, primary action, screen list, and any established design system. Do not add onboarding or extra screens to a one-screen request.
2. Establish shared typography, colors, spacing, icon language, navigation, safe-area treatment, and media style. Keep this design brief in context; create a separate document only when useful to the requested deliverable.
3. Map the requested screens and transitions. Show believable data, consistent navigation, and applicable empty/loading/error states when the flow needs them.
4. Use the available image-generation tool with a specific screen composition, legible copy, shared design choices, and relevant reference images. Device frames are optional presentation choices; prefer unobstructed UI when the user needs implementation references.
5. Inspect the result for readable text, coherent safe areas, realistic touch controls, visual hierarchy, and consistency across the flow. Regenerate only material defects within the requested scope. Stop when the requested screen set is delivered, or report a concrete tool limitation.

## Conditional references

- [Screen planning](references/screen-planning.md): multi-screen flows, platform choices, onboarding, and mockup presentation.
- [Visual language](references/visual-language.md): navigation, surfaces, imagery, iconography, and category-specific direction.
- [Screen quality](references/screen-quality.md): typography, media frames, consistency, and regeneration checks.

These references contain upstream defaults; user constraints and the workflow above take precedence. Use the host's image tool contract for editing and output delivery. If generation is unavailable, disclose that limitation and provide a prompt only as a fallback, never as a claimed generated image.

## Output contract

Deliver the requested images with a brief screen/flow description and any unresolved visual defects. Example: “Two checkout screens for an existing Android app” produces two coordinated screens using its established navigation and brand.

## Shared contract

Follow [the shared skill contract](../../shared/COMMON-CONTRACT.md) for scope, authorization, available tools, and verification evidence.
