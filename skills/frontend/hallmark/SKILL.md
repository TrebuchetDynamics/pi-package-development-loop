---
name: hallmark
description: "Structural anti-AI-slop design audit, redesign, or study from a page, URL, or screenshot. Use when the user explicitly invokes Hallmark or asks for its audit, redesign, study, or design-DNA workflow; use frontend-design for ordinary greenfield implementation."
version: 1.1.0
---

# Hallmark

A design skill for AI coding assistants. Makes the UIs they generate look made, not generated.

Hallmark is an opinionated structural design workflow. It encodes a tight set of rules — drawn from the consensus of the anti-AI-slop design field (Anthropic's frontend-design skill, the Claude cookbook on frontend aesthetics, and the 2026 "tactile rebellion" movement) — and refuses to let the model fall back to the defaults every LLM was trained on.

The differentiator: Hallmark insists on **structural variety**, not just visual variety. Two pages by Hallmark for two different briefs should not share the same hero → 3-feature → CTA → footer rhythm. They should feel like different sites, not different colour-swaps of the same template. See [`references/structure.md`](references/structure.md).

Use the available host tools. A provider named in upstream references is optional; do not configure or invoke an external image/model service merely because a recipe names it.

---

## Package workflow

Preserve existing project tokens, routes, content, and user decisions. Ask only for missing information that materially changes the design; do not repeat a design questionnaire when the brief is sufficient. Follow only the chosen mode and its relevant references. Audit and study are read-only. For implementation, verify responsive layout, keyboard/focus behavior, contrast, and applicable interaction states; report actual checks and limitations without invented scores.

## How to use this skill

Hallmark has one default behaviour and three explicit verbs.

| Invocation | What it does |
| --- | --- |
| *(default)* | The user asked you to design or build something new. Follow the **Design flow** below. |
| `hallmark audit <target>` | Read the target, score it against the anti-pattern list, return a ranked punch list. **Do not edit.** |
| `hallmark redesign <target> [--mood <name>]` | Take the target's content and intent, then redesign the visual structure **inside the existing implementation boundaries unless the user explicitly confirms a full rebuild.** New section rhythm, new heading placement, new component voice. Preserve existing routes, component ownership, copy intent, brand, and information architecture; replace only the visual/interaction layer needed for the requested scope. |
| `hallmark study <screenshot \| URL>` | The user pasted or attached an image of a design they admire, **or** pasted a URL to a live page. Extract the **DNA** — macrostructure, archetypes, type-pairing, colour anchor — and produce a diagnosis report, then optionally rebuild the user's content using the extracted DNA **or** emit a portable `design.md` of the DNA. Detection is automatic: a URL (`http://` / `https://` prefix) routes to URL mode; anything else routes to image mode. **URL mode** reads the page's HTML and CSS via WebFetch — it can name exact fonts and exact colour values, but can't judge rhythm. After the diagnosis, the user has three follow-ups: build with the DNA (handoff to default), lock the DNA into a portable `design.md` (opt-in via "lock the DNA" / "give me a design.md"), or stop at the diagnosis. **Never copies pixels. Refuses template-marketplace URLs. Tighter refusal layer for `design.md` emission than for the diagnosis itself — URL-mode emission requires attestation that the source is the user's own or a public reference for their own brand. Falls back to asking for a screenshot if the URL is auth-walled, a JS-only SPA shell, or otherwise un-readable.** Load [`references/study.md`](references/study.md) before this verb runs. |

If the user types anything that does not clearly map to `audit`, `redesign`, or `study`, treat it as default. If the user attaches an image or pastes a URL without a verb prefix, ask: *"Should I `study` this (extract the DNA), or should I treat it as a reference for a fresh build?"*

**Implementation safety rail.** Hallmark is a design skill, not a license to bulldoze a codebase. In any existing project:
- Never delete production files, route trees, component directories, or an old website unless the user explicitly asks for deletion or approves a file-level plan that lists the deletions.
- Default to in-place edits of the named files, or additive new components/tokens that are wired through the existing route. If the redesign would require removing multiple components, stop and ask for confirmation first.
- Treat PDFs, README files, `.md` briefs, docs, transcripts, and pitch decks as reference material. Do **not** copy them word-for-word into the page unless the user explicitly says to use that text verbatim.
- Before editing, state the exact files you expect to modify/create/delete. Deletions require explicit confirmation.

The default Design flow always picks a theme. By default it picks one of the **20 named themes** — the *catalog* — and rotates among them per the diversification rule. There is also a quiet *custom* branch that constructs a one-off OKLCH palette + free-font pairing for the brief; the custom route fires **only when the brief carries a creative-intent signal** (the user names a brand colour, names a multi-attribute vibe the catalog can't carry, or explicitly asks for a custom theme). For vanilla briefs, the user never sees the words "catalog" or "custom" — the catalog runs silently. See Step 1 (signal detection) and Step 2.6 (dispatch); the protocol lives in [`references/custom-theme.md`](references/custom-theme.md).

---

## Disciplines that hold across every verb

These six disciplines are **not** verb-specific. They apply to default Design, `audit`, `redesign`, `study`, and component-scope alike. They sit alongside the slop test, not inside one branch of it.

1. **Pre-emit self-critique.** Before handing back any output, score it 1–5 on six axes — Philosophy, Hierarchy, Execution, Specificity, Restraint, Variety. Anything **< 3** triggers a revision pass. Stamp the six scores at the top of the artifact (`/* Hallmark · pre-emit critique: P5 H4 E5 S4 R5 V5 */`). See [`references/slop-test.md`](references/slop-test.md) § Pre-emit self-critique.

2. **Honest copy — no fabricated content.** If the user did not supply a metric, do not invent one. Stat-led layouts, comparison rows, and proof bars must use real numbers, a placeholder (`—` plus a labelled grey block, "metric to confirm"), or a different macrostructure. *"+47 % conversion"*, *"trusted by 50,000+ teams"*, and *"10× faster"* are slop the moment they're invented. Same rule for testimonials, logos, and case-study counts. See [`references/anti-patterns.md` § Invented metrics](references/anti-patterns.md) and slop-test gate **46**.

3. **Locked tokens — no mid-render improvisation.** Once a theme is selected at Step 2.6, every colour and every `font-family` declaration in the artifact must reference a named token (`var(--color-accent)`, `font-family: var(--font-display)`). Inline OKLCH / hex / `rgb()` values, or a `font-family: "Some Font"` declaration that bypasses the token block, are not allowed. If a value is needed that doesn't exist as a token, lift it into the token block as a new named variable, then reference it. See [`references/anti-patterns.md` § Mid-render token improvisation](references/anti-patterns.md) and slop-test gate **48**.

4. **Re-drawn chrome forbidden.** Hallmark must not hand-build fake browser bars (URL pill + traffic-light dots), fake phone frames, fake code-block windows (mock title bar + dots wrapping a `<pre>`), or fake IDE chrome — the user's environment already supplies real chrome. Use real screenshots wrapped in a `<figure>` (with at most a hairline border), or omit the chrome and let the content stand on its own. See [`references/anti-patterns.md` § Re-drawn UI chrome](references/anti-patterns.md) and slop-test gate **47**.

5. **Mobile responsiveness — every emit verified at 320 / 375 / 414 / 768 px.** Hallmark's output must render flawlessly at all four widths. The non-negotiables: no horizontal scroll + root `overflow-x: clip` on both `html` and `body`, never `hidden` (gate 34); no two-line clickable text — buttons, primary nav links, footer links, breadcrumbs, CTAs (gate 49); image-bearing grid tracks use `minmax(0, 1fr)`, never bare `1fr` (gate 50); display headers wrap inside long words via `overflow-wrap: anywhere; min-width: 0` (gate 51); section heads collapse to one column on mobile across every theme variant (gate 52); radio-tab patterns don't scroll-jump (gate 53). See [`references/responsive.md` § Mobile — non-negotiable](references/responsive.md). This is a hard floor, not a wish list.

6. **Typography purity — no italic headers.** Headings and display type are always roman (`font-style: normal`). An italicised emphasis word inside an otherwise-upright heading (`Built to <em>think</em>`) is one of the most reliable AI tells; so is an all-italic display face on headings. Carry emphasis with weight, accent colour, or a drawn underline. Italic survives only as *body-copy* emphasis inside running paragraphs. See [`references/anti-patterns.md` § Italic headers](references/anti-patterns.md) and slop-test gate **38a**.

---

## When the brief is a component, not a page

For a single component, read [the component workflow](references/component-workflow.md). Preserve the surrounding tokens and implement only the states applicable to that component; do not add page-level artifacts.

## Design flow (default)

For a new page or an explicitly requested Hallmark build, read [the page workflow](references/page-workflow.md). Infer answered brief details from context, then build and verify within the requested scope.

## `hallmark audit`

Load [`references/verbs/audit.md`](references/verbs/audit.md) and follow it.

---

## `hallmark redesign`

Load [`references/verbs/redesign.md`](references/verbs/redesign.md) and follow it.

---

## `hallmark study`

For reference analysis, read [the study workflow](references/study-workflow.md) and its linked study guidance. Return the diagnosis first; implementation or saved design-system work requires that requested follow-up.

## Output contract & scope

Load [`references/contract.md`](references/contract.md) once, at handoff time, for the full output contract and scope-of-skill rules.

## Shared contract

Follow [the shared skill contract](../../shared/COMMON-CONTRACT.md) for repo study, dirty-worktree hygiene, verification evidence, safe handoffs, and safety defaults.
