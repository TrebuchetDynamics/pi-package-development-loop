---
name: ui-ux-pro-max
description: "Deep web/mobile design-system and accessibility guidance covering color, typography, layout, motion, dashboards, and interaction quality. Use for design decisions or review, not primary implementation when a build/redesign skill fits."
---

# UI/UX Pro Max

Use the bundled design data to support a concrete design decision or review. Preserve the product's existing platform and design system; do not turn a scoped accessibility or color question into a full redesign.

## Workflow

1. Inspect the requested surface, audience, current tokens/components, and relevant states. Identify the decision to resolve: layout, color, type, navigation, interaction, accessibility, or visualization.
2. Resolve `SKILL_DIR` to the absolute directory containing this `SKILL.md`. If Python is available, search the bundled data using the read-only helper. Run it from the target project only when the requested operation intentionally writes there.

```sh
python3 "$SKILL_DIR/scripts/search.py" "<product and visual direction>" --design-system -p "Project Name"
python3 "$SKILL_DIR/scripts/search.py" "<specific question>" --domain ux
```

3. Treat results as suggestions to check against the actual product, not authoritative proof of accessibility or current browser support. Use the project's stack; request a stack-specific search only for that stack.
4. Recommend the smallest set of changes that resolves the design problem. When implementation was requested, apply them through the selected build/redesign workflow, preserving content and behavior.
5. Verify applicable focus, keyboard, contrast, touch, responsive, and loading/error behavior in the actual artifact. Distinguish measured or observed checks from untested recommendations.

## Conditional references

- [Rule catalog](references/rule-catalog.md): consult the category relevant to the current decision; do not load every platform's rules for one component.
- [Search workflow](references/search-workflow.md): CLI examples, domain/stack choices, output formats, and optional persistence.
- [Delivery checklist](references/delivery-checklist.md): relevant visual and interaction checks before reporting implementation complete.

If Python is unavailable, use the relevant reference directly and disclose that the data search was not run. Do not install system software merely to answer a design question. `--persist` writes design-system files; use it only for a requested saved design system, after checking existing files.

## Output contract

For review, return evidence-backed findings with concrete fixes. For a design-system request, return tokens, rationale, and the requested artifact path. For implementation, name changed files and actual validation. Example: a chart accessibility review checks keyboard navigation and text alternatives without replacing the app's visual identity.

## Shared contract

Follow [the shared skill contract](../../shared/COMMON-CONTRACT.md) for scope, authorization, available tools, and verification evidence.
