# Composition

Read only the sections relevant to the current task. Paths and commands are relative to the skill directory unless stated otherwise. The entrypoint workflow and user constraints take precedence over these reference defaults.

## 1. ACTIVE BASELINE CONFIGURATION

- DESIGN_VARIANCE: 8
  `(1 = rigid / symmetrical, 10 = artsy / asymmetric)`
- VISUAL_DENSITY: 4
  `(1 = airy / gallery-like, 10 = packed / intense)`
- ART_DIRECTION: 8
  `(1 = safe commercial, 10 = bold creative statement)`
- IMPLEMENTATION_CLARITY: 9
  `(1 = loose moodboard, 10 = very codeable UI reference)`
- IMAGE_USAGE_PRIORITY: 9
  `(1 = mostly typographic, 10 = strongly image-led)`
- SPACING_GENEROSITY: 8
  `(1 = compact / tight, 10 = very spacious / breathable)`
- LAYOUT_VARIATION: 8
  `(1 = same anchor repeats, 10 = bold composition variety across sections)`
- CONVERSION_DISCIPLINE: 8
  `(1 = pure art moodboard, 10 = clear funnel + premium design balance)`

AI Instruction:
Use these as global defaults unless the user clearly asks for something else.
Do not ask the user to edit this file.
Adapt these values dynamically from the prompt.

Interpretation:
- **Adaptation priority**: the user's brief always overrides defaults. Read the prompt carefully, then adjust dials, hero scale, background mode, gradient use, and composition variety to match — never force a recipe that contradicts the brief.
- If the user says "clean", reduce density and increase clarity.
- If the user says "crazy creative", increase variance and art direction.
- If the user says "premium SaaS", keep clarity high and art direction controlled.
- If the user says "editorial", allow stronger type and more asymmetry.
- Bias toward stronger visual concepts, not safe layouts — but never against the brief.
- Use imagery as a core design material — including as **full-bleed backgrounds**, not only as inline assets, **when the brief allows it**.
- Vary composition: do not default to "text left, image right". Move text to bottom-left, center, top-right, etc. across sections.
- Keep sections breathable. Do not over-pack the page.
- Prefer slightly more whitespace between sections than default.
- Stay conversion-aware: every section has a job (hook / proof / educate / convert).

### Brief-to-direction mapping
Read the brief. Then bias the picks like this:

If the user says **"minimalist" / "clean" / "typography-only" / "swiss" / "ultra simple"**:
- Hero Scale: Mini Minimalist
- Background Mode: solid surfaces, subtle texture, optional ONE color-blocked diptych
- Gradients: skip or use only the softest tonal gradient
- Composition: stacked center, generous negative space
- Skip the "must include full-bleed" rule

If the user says **"editorial" / "magazine" / "art-directed" / "fashion"**:
- Hero Scale: Mid Editorial or Giant Statement
- Background Mode: editorial side-image, duotone treated image, atmospheric photo grade
- Gradients: subtle tonal grades only
- Composition: off-grid editorial offset, asymmetric pulls
- Strong typography contrast

If the user says **"cinematic" / "atmospheric" / "premium" / "luxury" / "bold"**:
- Hero Scale: Giant Statement
- Background Mode: full-bleed image with tonal overlay, soft radial vignette + product, micro-noise gradient
- Gradients: cinematic palette-matched welcomed
- Composition: bottom-left over background image, centered low, image-as-canvas

If the user says **"SaaS" / "product" / "dashboard" / "fintech" / "infra"**:
- Hero Scale: Mid Editorial
- Background Mode: solid + inline asset, flat block + detail crop, occasional editorial side-image
- Gradients: very subtle, palette-matched only
- Composition: clear product framing, trust-driven anchors
- Slightly higher implementation clarity

If the user says **"agency" / "creative studio" / "portfolio"**:
- Hero Scale: Giant Statement OR Mini Minimalist (decisive)
- Background Mode: vary boldly (full-bleed image, color-blocked diptych, duotone)
- Gradients: editorial color washes acceptable
- Composition: off-grid, poster-like

If the user says **"e-commerce" / "shop" / "store" / "product page"**:
- Hero Scale: Mid Editorial with strong product focus
- Background Mode: full-bleed product photo, soft radial vignette + crop, flat block + detail
- Gradients: subtle, never competing with product
- Composition: product-led; CTAs unmistakable

If the brief is silent on style:
- Use defaults from §1 + §2 with confident background variety
- Pick one Hero Scale decisively, do not split the difference

Never force backgrounds, gradients, or full-bleed treatments where the brief asks for restraint. Never strip them out where the brief asks for atmosphere.

---

## 2. THE COMBINATORIAL VARIATION ENGINE
To avoid repetitive AI-looking output, internally choose one option from each category based on the prompt and commit to it consistently.

Do not mash everything together into chaos.
Pick a strong combination and execute it clearly.

### Theme Paradigm
Choose 1:
1. Pristine Light Mode
   Off-white / cream / paper tones, sharp dark text, editorial confidence.
2. Deep Dark Mode
   Charcoal / graphite / zinc, elegant glow only when justified.
3. Bold Studio Solid
   Strong controlled color fields like oxblood, royal blue, forest, vermilion, or emerald with crisp contrasting UI.
4. Quiet Premium Neutral
   Bone, sand, taupe, stone, smoke, muted contrast, restrained luxury.

### Background Character
Choose 1:
1. Subtle technical grid / dotted field
2. Pure solid field with soft ambient gradient depth
3. Full-bleed cinematic imagery with proper contrast control
4. Quiet textured paper / material / tactile surface feel

### Typography Character
Choose 1:
1. Satoshi-like clean grotesk
2. Neue-Montreal-like refined grotesk
3. Cabinet / Clash-like expressive display
4. Monument-like compressed statement typography
5. Elegant editorial serif + sans pairing
6. Swiss rational sans with very strong hierarchy

Never drift into boring default web typography energy.

### Hero Architecture
Choose 1:
1. Cinematic Centered Minimalist
2. Asymmetric Split Hero
3. Floating Polaroid Scatter
4. Inline Typography Behemoth
5. Editorial Offset Composition
6. Massive Image-First Hero with restrained text

### Section System
Choose 1 dominant structure:
1. Strict modular bento rhythm
2. Alternating editorial blocks
3. Poster-like stacked storytelling
4. Gallery-led visual cadence
5. Swiss grid discipline
6. Asymmetric premium marketing flow

### Signature Component Set
Choose exactly 4 unique components:
- Diagonal Staggered Square Masonry
- 3D Cascading Card Deck
- Hover-Accordion Slice Layout
- Pristine Gapless Bento Grid
- Infinite Brand Marquee Strip
- Turning Polaroid Arc
- Vertical Rhythm Lines
- Off-Grid Editorial Layout
- Product UI Panel Stack
- Split Testimonial Quote Wall
- Oversized Metrics Strip
- Layered Image Crop Frames

### Motion-Implied Language
Choose exactly 2:
- scrubbing text reveal energy
- pinned narrative section energy
- staggered float-up energy
- parallax image drift energy
- smooth accordion expansion energy
- cinematic fade-through energy

### Composition Anchor (per-section)
The **left-text / right-image** layout is allowed, but it is the most overused AI pattern — do not use it as the default. Reach for it only when it is the genuinely best fit.

Each section picks 1 anchor; across the site at least 3 different anchors must appear; vary the hero so the page does not open on the AI default.
- Centered statement
- Top-left lead, support bottom-right
- Bottom-left text over background image
- Bottom-right CTA cluster
- Left-third caption + right-two-thirds visual (classic — use sparingly, never twice in a row)
- Right-third caption + left-two-thirds visual (inverted classic)
- Centered low (text in lower 40% over hero image)
- Off-grid editorial offset (asymmetric pull)
- Stacked center (label / headline / sub / CTA all centered, ultra minimalist)
- Image-as-canvas with text overlaid in a clean safe area

### Background Mode (per-section)
Pick 1 per section; vary across the page so it is never all the same mode. Be **confident** with backgrounds — they are a primary tool, not a risk.
- Solid surface with inline asset
- Subtle texture / paper / grid as background
- Full-bleed image background with tonal overlay (text remains highly readable)
- Editorial side-image (50/50, 60/40, 40/60 — invertible)
- Image as the entire visual + text overlaid in a clean safe area
- Flat color block + small product / detail crop as accent
- Cinematic tonal gradient (palette-matched, low chroma, professional)
- Atmospheric photo with strong color grade (single-tone graded for brand mood)
- Duotone treated image (two-color photo treatment, palette-locked)
- Soft radial vignette + product crop (luxury / editorial feel)
- Micro-noise gradient over solid (premium tactile depth, not flashy)
- Color-blocked diptych (two flat fields meeting, modernist)

### CTA Variation
Pick the CTA style that fits each section, not a default pill every time:
- Classic primary pill
- Outline / ghost
- Underlined inline link with arrow
- Banner-style full-width CTA
- Oversized headline + tiny CTA hint
- CTA as caption under a strong visual

Across the site, vary CTA style at least once. The page's primary action stays unmistakable.

### Hero Scale (per-page)
Pick 1 — must match brand mood:
- Giant Statement Hero (massive type, large image, dominant first viewport)
- Mid Editorial Hero (balanced type/image, cinematic but not screen-filling)
- Mini Minimalist Hero (tiny logo + short statement + thin CTA, almost no image, lots of negative space)

Mini does not mean weak — it means confident restraint.

### Narrative / Concept Spine
Pick 1 and let it thread through visuals and short copy across the page.
- Artifact / collectible — proof, specimen, treasured object framing
- Journey / pilgrimage — directional flow, waypoint sections, roadmap feeling
- Tool / precision instrument — machined detail, calibrated UI, tactile controls
- Living system / garden — organic growth metaphor, branching layout, nurtured tone
- Stage / spotlight — theatrical contrast, performer + audience framing
- Archive / dossier — indexed rows, captions, understated authority

### Second-Read Moment
Pick exactly 1 unobvious but legible motif and place it deliberately, once across the page:
- asymmetric bleed that still respects hierarchy
- one oversized punctuation or numeral serving structure
- a single unexpected material switch (paper vs gloss vs metal accent)
- a narrow vertical side-rail editorial note style
- a macro crop that carries brand color naturally
Avoid gimmick-for-gimmick: the moment must aid scan order or brand recall.

Important:
These are not coding instructions.
They are visual-direction cues the generated design should imply.

---

## 3. FRONTEND REFERENCE RULE
Every generated image must clearly communicate:
- layout
- section hierarchy
- spacing
- typography scale
- visual rhythm
- CTA priority
- component styling
- image treatment
- overall design system

A developer or coding model should be able to look at the image and understand how to build it.

Do not produce vague abstract artwork when the request is for frontend.

---

## 4. HERO MINIMALISM RULES
The hero must feel cinematic, clear, and intentional.

### Hero Composition Bias
The **left-text / right-image hero is the most overused AI hero pattern**. It is allowed, but it should not be your default starting point.

Prefer one of these instead, unless left-text / right-image is genuinely the strongest fit:
- Centered statement over full-bleed image (text in lower 40%)
- Bottom-left text over background image
- Bottom-right text over background image
- Top-left lead, support bottom-right
- Stacked center (label / headline / sub / CTA all centered)
- Image-as-canvas with text overlaid in a clean safe area
- Right-text / left-image (inverted classic)
- Off-grid editorial offset
- Mini Minimalist Hero (tiny logo + short statement + thin CTA, mostly negative space)

### Pre-output check
Before rendering the hero image, ask yourself: "Am I drafting the default text-left / image-right layout out of habit?" If yes, prefer a different anchor from the list above unless the brief or brand truly requires the classic.

### Absolute Hero Rules
- the hero must feel like a strong opening scene
- keep the hero composition clean
- do not overcrowd the first viewport
- the main headline must feel short and powerful
- headline should usually read like 5-10 strong words, not a paragraph
- keep supporting text concise
- prioritize negative space and contrast
- avoid stuffing the hero with pills, fake stats, badges, tiny logos, and nonsense detail

### Headline Rule
The H1 should visually read like a premium statement.
Do not let it feel long, weak, or overly wrapped.

### Typography Execution
Prefer:
- medium / normal / light elegance
- tight tracking
- controlled line count
- strong scale contrast

Avoid:
- random extra-bold shouting everywhere
- gradient text as a lazy premium effect
- 6-line startup headings
- text treatment that looks generated

### Graphic Restraint
Do not default to:
- giant meaningless outline numbers
- cheap SVG-looking filler graphics
- generic AI blobs
- random orb clutter

Use:
- typography
- image crops
- real layout tension
- premium materials
- strong framing
instead.

---

## 5. IMAGE COUNT & PAGE SLICING

### THIS IS THE PRIMARY OUTPUT RULE
Generate **one separate horizontal image PER section**. Always.

- never combine multiple sections in a single image
- never return a single tall slice that contains the whole page
- never return one "best" image and skip the rest
- never replace several sections with one collage

If the request is ambiguous about section count, **default high**:
- "hero" -> 1 image
- "landing page" / "site template" -> default to 6 sections -> 6 images
- "full website" -> default to 8 sections -> 8 images
- "marketing site" -> default to 8 sections -> 8 images
- "product page" -> default to 6 sections -> 6 images
- "portfolio" -> default to 6 sections -> 6 images

If the model can only render one image per call, generate them **sequentially in the same response**, one after the other, labeled "Section X of N: <name>" until the full set is delivered.

### Format
- Always horizontal (16:9, 16:10, or 21:9 depending on density)
- Each image renders one focused section in high fidelity
- Hero usually 16:9 or 21:9; narrower content sections may be 16:10

### Counting rule
- 1 section -> 1 horizontal image
- 4 sections -> 4 horizontal images
- 8 sections -> 8 horizontal images
- 12 sections -> 12 horizontal images

Do not collapse multiple sections into one tall slice. Section size and density may still vary, but the canvas stays horizontal and **one section per frame**.

### Section size variety
Across the site, mix section ambition deliberately:
- some sections are large, content-rich, art-directed
- some sections are mini, ultra minimalist, mostly negative space
- some sections are medium editorial blocks

This rhythm creates a premium scrollscape, not uniform slabs.

### Continuity Rule
Across all per-section images, enforce one brand world:
- same palette and accent logic
- same typography family and scale
- same CTA family (style variations are fine, identity is not)
- same border radius language
- same image treatment (color grade, materials, framing)
- same tonal voice in any short copy

A viewer scrolling through all frames must read them as one site.

---

## 6. CREATIVITY ESCALATION RULE
The design must show real creative ambition.

Do not settle for the first obvious layout solution.
Push the work beyond generic SaaS patterns.

Actively increase at least 3 of these:
- stronger composition
- more distinctive typography
- more confident scale contrast
- more memorable hero concept
- more interesting image treatment
- more expressive section rhythm
- more original framing / cropping
- more art-directed visual tension
- more surprising but clear layout structure

Creativity must feel intentional, not chaotic.

Do:
- make bold but controlled design decisions
- use asymmetry when it improves the page
- create visual moments that feel premium and memorable
- make the page feel designed, not auto-generated

Do not:
- default to safe template layouts
- repeat the same block structure too often
- confuse creativity with clutter
- make the page overly dense

---

## 7. IMAGE-FIRST ART DIRECTION
This skill must actively use images.

Images are not optional decoration.
Images are a core part of the frontend design language.

Strongly prefer:
- art-directed photography
- product imagery
- editorial imagery
- image crops
- framed image panels
- layered image compositions
- image-led hero sections
- image-supported storytelling blocks

Use images to:
- create visual hierarchy
- break up text-heavy layouts
- build mood and brand character
- support section transitions
- make the design easier to interpret and implement

Important:
- the design should not become text-only or card-only unless the user explicitly wants that
- if a page has multiple sections, several sections should meaningfully include imagery
- if a hero exists, it should usually contain a strong visual image, product visual, or art-directed media element
- imagery should feel premium and intentional, not like stock filler

Avoid:
- tiny useless thumbnails
- random decorative images with no structural role
- one single image and then a completely text-heavy rest of page
- overusing fake UI panels instead of real visual variety

---
