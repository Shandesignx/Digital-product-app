# REVEL® — Reference Analysis, Motion Specifications & Premium Upgrade Brief

**Purpose:** Give a coding assistant a precise, production-oriented specification for improving the supplied REVEL website using the attached Lagunitas-inspired reference recording and original transparent can asset.

**Deliverable type:** Functional, responsive, premium, scroll-controlled product storytelling website — not a video, static mockup, or collection of unconnected animations.

**Source precedence:** (1) attached screen recording as evidence of visible aesthetic/sequence, (2) attached REVEL can as exact product/brand visual, (3) supplied REVEL website source as editable implementation baseline, (4) this brief for proposed technical upgrades. In conflicts, preserve the actual assets and explicit user instructions. Do not copy original Lagunitas logos, layouts word-for-word, site copy, or label graphics.

## A. Actual reference — what can and cannot be established

- The MP4 `Record_2026-11-08-03-45-30_8b1cfbb769bd52fc36fa25a4fcc64305.mp4` is a roughly **5 minute 53 second portrait mobile screen recording**. Its beginning shows a Pinterest presentation of a roughly **15-second** website-design showcase for Lagunitas IPA; the rest mostly shows exploration of other designs on Pinterest. Focus inspection on that initial embedded showcase, not the later feed.
- The showcase visibly contains: warm cream/off-white canvas, restrained black navigation, very large condensed dark-red headline, product bottle over typography, red/black editorial blocks, framed specifications, photorealistic bottle scaling/tilting and repositioning, giant `MOUTHFEELS` text, small inset imagery, irregular splatter-style flavor notes, and a `YEAR ROUND` lineup of products.
- Visible content progression in the embedded showcase is approximately: (1) angled bottle over red `UNLIMITED RELEASE IPA` lettering; (2) more upright centered bottle with `INDIA PALE ALE` and a facts card; (3) `MOUTHFEELS` page, thumbnail photo and tasting description; (4) ink-splash ingredient/taste callouts, occasional crop of a poured beverage; (5) `YEAR ROUND` product lineup; (6) lower lifestyle/content section. This is **visual sequence**, not confirmed site DOM structure.
- The reference has a premium printed-editorial aesthetic. A bottle appears above some headings, integrated with paragraphs, cards, irregular graphic shapes and photographic blocks. Large headings are allowed behind the object, with small copy arranged around it.
- **Not recoverable from the recording:** original CSS/Three.js, real-time user scroll input mapping, camera focal length, exact easing curves, section heights, original 3D topology, lighting rig, GPU shaders, physical scroll velocity, original breakpoints, and verified frame rates. All technical quantities below are proposed implementation targets, **not measured attributes of the original**.

## B. Current REVEL assets and implementation — inspection findings

**Assets**
- `revel_red_berry_sparkling_can.png` or `public/revel-can.png`: single isolated red drink-can render, silver lid and rim, condensation and original REVEL label. Treat as the source of truth for appearance and typography. Preserve visible label details instead of redrawing them loosely.
- Original color reference shows four recommended brand reds: `#AA2829`, `#E3171A`, `#E12E30`, `#AA061B`.
- Original code bundle: `revel-vintage-website-source.zip` / `revel-vintage-website` containing `components/RevelExperience.tsx`, `app/globals.css`, and Next.js App Router project; static site ZIP and single-file HTML are also available.

**Current behavior**
- Five scroll chapters: `THE REVEAL`, `THE ATTITUDE`, `THE FLAVOUR`, `THE COLOUR`, `THE FINALE`; chapter content crossfades under one floating product cutout.
- `Lenis` smooth wheel handling plus a custom `requestAnimationFrame` loop interpolating product x/y, scale, 2D roll, faux `rotateY`, scene opacity and content translate; `GSAP` currently handles the brand entrance.
- Long sticky stage, responsive chapter positions, vintage red/cream typography, menu overlay, footer and progress UI.
- Existing implementation is **2.5D image compositing**, not real spatial 3D. The photo cannot reveal real unseen sides/back or deliver a physically accurate 360° orbit.

**Priority improvements**
1. Unify scroll progress, state and timelines; avoid redundant scroll smoothing. Add ScrollTrigger only if it improves determinism/maintainability, and synchronize it correctly with Lenis.
2. Build richer transitions than simple opacity fades while retaining a continuous product trajectory. Add text masks, image wipes, staggered copy reveals and controlled parallax.
3. Keep the subject visually registered on its optical center when scaling or moving; preserve label legibility and avoid distorted fake 3D yaw.
4. Add reference-like *information architecture*: product fact card, flavor-note splashes, small editorial photo/inset, an impactful large-text chapter and a final product/lifestyle story section. Do not claim multi-product flavors without assets.
5. Fix adaptive progress meter transforms (horizontal track on mobile must scaleX, desktop vertical track scaleY).
6. Verify both delivered project source and bundled static version in the browser, with keyboard/touch/reduced-motion fallback and motion consistency across viewport sizes.

## C. Creative direction / visual design system

**Positioning:** Modern craft-beverage experience with nostalgic print-ad energy, editorial precision, premium art direction and believable product materials. New brand: `REVEL® RED BERRY` — **not** the original brewery.

**Palette (locked brand anchors)**
- Oxblood / editorial red: `#AA2829`
- Bright signal red: `#E3171A`
- Berry pop red: `#E12E30`
- Deep crimson: `#AA061B`
- Supporting cream/paper (design proposal; not sampled from video): `#EEE9DC`
- Supporting pale cream: `#F7F1E5`
- Warm near-black ink: `#211B18`
- White text for deep-red chapters: `#FFF9EF`

Use mostly paper + ink with strategic large red typographic passages; reserve full crimson backgrounds for 1–2 punctuation scenes. Avoid using all four reds in equal proportions in every scene.

**Typography**
- Hero display: exceptionally bold and condensed, uppercase, tight tracking and compact line-height (Anton, Barlow Condensed Black, or commercially licensed equivalent).
- Editorial heading: strong condensed grotesk; occasional italic high-contrast serif accent (e.g. Playfair Display) for vintage contrast.
- Supporting data/captions: mono or narrow neutral font (DM Mono or equivalent) with measured letter spacing.
- Body text: clear contemporary sans (DM Sans or equivalent). Avoid distressing all body text.
- Text must remain semantic, sharp, selectable and accessible; do not render entire paragraphs as raster textures. Headline texture may be achieved with a subtle isolated overlay or masking.

**Layout rules**
- Desktop: 12-column editorial grid, spacious outer gutters about 3–5vw; intentional, asymmetrical copy blocks, object in front of giant display type.
- Mobile: single-column editorial rhythm, smaller headings, product center preserved and repositioned where necessary; never allow the can to cover the primary CTA or critical explanatory text.
- Fluid type via `clamp()`, responsive containment, 100svh/100dvh as appropriate, safe area support on Android/iOS, soft drop shadow physically anchored to the can.
- Graphic accents: old print registration lines, numerals, seals, small ruled cards, editorial footnotes, occasional hand-stamped arrows, 2–3 controlled jagged ink/paper splash shapes, very restrained vignette/grain and halftone texture.

## D. Reference-driven experience sequence (recommended expansion)

This seven-beat timeline is an enhancement proposal; the source video does not prove seven actual website sections. Create a single sticky story stage controlled by scrolling, with non-sticky lead-in/out as needed. Percentages refer to normalized story progress and are tunable.

| Phase | Scroll range | Visual / content | Product composition | Motion |
|---|---:|---|---|---|
| 00 / Opening | 0–14% | Cream paper, giant red `A LITTLE LOUDER`, issue number and red seal | Large can floating front-center at slight lean | Soft scale 0.92→1.04, roll -10°→-4°, very gentle translation, headline mask-up reveal |
| 01 / Introduction | 14–28% | `MEET THE RED BERRY` plus original brand line and short description | Can shifts right leaving left column clear | Smooth continuous x/y interpolation, right-side details card wipe, type tracking settles |
| 02 / Product details | 28–43% | Framed data panel, `355 mL` and concept-only label descriptors; fine print | Upright, stable and prominent | Tactile spec reveal, pointer-led details (not invisible pins), label-safe zoom, restrained shadow change |
| 03 / Mouthfeel | 43–58% | Giant `THE GOOD KIND OF FIZZ`, small lifestyle/photo slot and editorial story | Can passes over headline but not body copy | Headline behind can; letters masked/staggered, image uncover, camera-like lateral parallax |
| 04 / Flavour notes | 58–73% | Splash-shaped `BRIGHT`, `BERRY`, `SPARKLE` labels, supporting small images | Product pulled toward center and fractionally forward | Callouts bloom at staggered scroll points, subtle separate layers, minimal splash morph if feasible |
| 05 / Signature reds | 73–87% | Bold full-red interlude, swatches of four locked reds and large statement | Hero can counter-rotates and moves off-center | Background color transition without flash, scale/crop carefully controlled, editorial type wipe |
| 06 / Final moment | 87–100% | Hero recap, `MAKE IT A REVEL MOMENT`, CTA and restart control | Can returns nearly upright to dominant center | Settled finish, smooth deceleration, no snapping or sudden reset |

**On-screen copy is creative placeholder, not a verified food-product claim.** The can image visibly contains label text including `RED BERRY`, `SPARKLING DRINK`, `ZERO SUGAR`, and `355 mL` but do not invent a nutrition panel, ingredients, sustainability claims, proprietary manufacturing methods, certifications or availability. Leave unverified claims configurable and off by default.

## E. Motion choreography and exact implementation rules

**Continuous trajectory**
- Compute one authoritative normalized `storyProgress ∈ [0,1]` from the sticky section; map it through one continuous set of transform keyframes. Do not reset the product DOM node on chapter changes.
- Favor `translate3d`, `rotateZ`, `scale`, and very limited 2.5D perspective only if it does not stretch the label or make the flat PNG obvious. Default no 360° spin using only PNG.
- Recommended movement ranges (tunables, not extracted): roll within roughly ±12°; main scale 0.85–1.25 except intentional cinematic crops; lateral travel generally within 20–28vw; easing `power2.inOut` or smoothstep, and gently damped progress changes.
- Product optical center remains stable; no jumping as text scenes enter. Shadow transforms and highlight overlays follow product movement. Avoid excessive `filter: blur` on the source image.
- Build one progress-based GSAP ScrollTrigger timeline using `scrub` (or one custom RAF progress loop) and do not run two competing smoothing loops. If using Lenis, connect `lenis.on('scroll', ScrollTrigger.update)`, drive `lenis.raf` from GSAP ticker, and account for time units; or keep native scroll plus ScrollTrigger. Pick one approach and explain it.
- All stage animations derive from scroll position and are reversible. Fast scrolling, anchor navigation, back/forward navigation and reverse scrolling must render consistent intermediate states.

**Typography and scene effects**
- Giant condensed display words reveal with clip/mask from below or across, slight scale correction and letter-spacing easing; keep text as DOM, not video.
- Editorial paragraphs stagger by line/group; preserve readable durations and contrast. Avoid typewriter animation for paragraphs.
- Reference-like splash shapes can be layered SVG vectors with minimal morph/scale/opacity and parallax; do not claim fluid simulation. Keep splashes behind body copy unless deliberate.
- Data cards slide or wipe into a ruled frame; numeric figures may count up once when scrolled into view, but scroll reversal must not leave impossible values.
- Use 2–3 distinct transition motifs maximum (mask/wipe, lateral parallax, object tilt) rather than throwing every effect into every scene.
- Subtle paper noise should be static or gently drifting, low opacity and contrast, preferably CSS/SVG tile. No full-screen per-frame canvas noise on mobile.
- Add cursor hover only for desktop interactive controls; do not hijack user scroll, force mandatory scroll snapping, autoplay audio or add seizure-risk flashes.

**Enhanced 3D option**
- Phase A — **Mandatory**: use provided transparent PNG, preserve high detail and matte/metallic highlights; subtle tilt and camera-language movement within its single view. Do not simulate seeing a back label.
- Phase B — **Only if genuine assets supplied/created with approval**: create an actual can-shaped mesh in Three.js / R3F, wrap a faithful label texture, use a real silver rim/tab geometry, physically based metal material, proper normals and roughness, camera orbit, contact lighting and soft reflections. Match original front label accurately. To deliver real 360°, require multi-view product images or editable label artwork/UV textures; do not reconstruct unseen label details as fact.
- A conditional WebGL enhancement must have a reliable 2.5D fallback for reduced motion, unavailable WebGL, low-end devices and slow networks.

## F. Engineering architecture

**Preferred stack:** Next.js App Router, React, TypeScript, modern CSS/Tailwind if already present, GSAP with ScrollTrigger, Lenis (optional), Three.js/R3F only for a genuine mesh. Respect existing working code instead of discarding it.

**Suggested modules:**
```
app/
  page.tsx
  layout.tsx
  globals.css
components/
  Experience.tsx
  EditorialScene.tsx
  CanStage.tsx
  ScrollProgress.tsx
  SceneNavigation.tsx
  ReducedMotionPage.tsx
lib/
  sceneConfig.ts
  motion.ts
  media.ts
public/
  revel-can.png
  textures/paper-grain.svg
  imagery/ (only real supplied/licensed assets)
docs/
  reference-notes.md
  asset-map.md
  acceptance-checklist.md
```

**Timeline architecture:** `sceneConfig.ts` carries scenes, text, section boundaries, x/y/scale/roll targets, entrance offsets and palette; all values can be edited without rebuilding core animation plumbing. Each scene owns semantic content and entrance/exit effects, while one global CanStage renders the product continuously.

**Performance targets (goals, not promises):** 60fps on capable desktops, fluid mobile with graceful quality reduction; LCP ≲2.5s under appropriate test conditions; CLS <0.1; INP <200ms; no horizontal overflow; responsive from 320px through 1920px. Optimize DPR and texture dimensions on mobile; respect battery saver where detectable. Animate transforms and opacity only where practicable. Avoid unnecessary layout reads in RAF. Lazy-load secondary media; pre-load the hero can; use image aspect ratios to prevent layout shift.

**Accessibility:** `prefers-reduced-motion` offers simplified static/short-transition storytelling; logical headings; real alt text and focus order; visible focus rings; 44px touch targets; sufficient contrast and readable mobile font sizes; optional no-JS readable fallback; keyboard navigation without focus trapping errors.

**Testing:** Verify desktop viewport 1440×900 and mobile 390×844 minimum, plus 320px, 768px and 1920px. Browser checks: Chromium, Android Chrome, Safari/WebKit if available. Capture screenshots at opening, each chapter midpoint and footer; compare to reference for visual vocabulary, not pixel-for-pixel brand duplication. Test forward scroll, reverse scroll, wheel, touch momentum, anchor navigation, resize, menu and prefers-reduced-motion. Check console errors, missing images, hydration warnings, focus behavior and scroll restoration. Run `npm install`, `npm run build`, and browser automation; do not claim results that weren't actually tested.

## G. Priority plan and acceptance conditions

**P0 — must ship**: faithful attached REVEL can; vintage editorial composition; responsive continuous single product path; readable text; cinematic intro/mid/outro; no jank; fully wired menu/CTA; accessible reduced-motion; verified build; complete source.

**P1 — premium polish**: branded custom splashes, subtle halftone, dynamic shadow, chapter mask reveals, per-scene deliberate parallax, real mobile composition, continuity passes and performance profiling.

**P2 — optional / asset dependent**: photorealistic true 3D can, physical refraction/condensation, custom shaders, vector label UV and side/back details, complex WebGL postprocessing, optional audio toggle only if the user explicitly requests sound.

**Done means:** the site works as a website, not an exported film; the product remains consistent in every scene; scroll is reversible and responsive; no text collisions on 390px mobile; all navigation works; references remain distinguishable from new creative work; working source and documented commands are delivered; remaining uncertainties are explicitly disclosed.

---

# MASTER BUILD PROMPT — COPY FROM HERE

**Role:** You are a senior Creative Technologist, Award-Winning Art Director, Senior Motion Designer and Staff Frontend Engineer. You must upgrade my existing REVEL product website into a premium, production-ready scroll-controlled 2.5D/3D editorial experience inspired by the attached reference recording, while keeping my source code and brand assets editable.

## Attached input files — read before coding
1. **Original reference screen recording:** `Record_2026-11-08-03-45-30_8b1cfbb769bd52fc36fa25a4fcc64305.mp4` (the useful beverage-site showcase is at the beginning; later material is primarily Pinterest browsing). Inspect the visible product positioning, headline staging, supporting cards, ink splashes, information rhythm, and product collection section. Extract a storyboard with evidence and uncertainty. Do not pretend to recover hidden source-code timing from a screen recording.
2. **Original product:** `revel_red_berry_sparkling_can.png` or `revel-can.png`. Use this exact high-resolution isolated red can with original visible label, metal lid and condensation.
3. **Brand color-reference image:** `74892.jpg` or the uploaded screenshot with hex codes `#AA2829`, `#E3171A`, `#E12E30`, `#AA061B`. Use these as design anchors, not as source imagery.
4. **Existing website:** `revel-vintage-website-source.zip`, or the unzipped Next.js project, plus `revel-vintage-demo.html` / `revel-vintage-static-site.zip` if available. Audit these files and improve them **in place**. Do not restart from a generic landing page or discard existing functional behavior.
5. **This specification:** `REVEL_Reference_Analysis_And_Upgrade_Specification.md`. Treat it as implementation goals; the video and product remain ground-truth assets.

## Main objective
Create an original website for **REVEL® RED BERRY**, evoking the reference's premium vintage beer-ad editorial pacing but reinterpreted for the red beverage can. The website must offer the feeling that scrolling art-directs a continuous film — product sliding, lifting, subtly tilting and scaling across enormous condensed typography, card details, photographic insets, tasting-note splashes and surprising red/cream transitions. The experience must be elegant, legible, interactive, reversible and stable on mobile.

## Art direction
Use a restrained vintage-print design system: warm cream paper, powerful `#AA2829` / `#E3171A` headlines, `#E12E30` accents, deep `#AA061B` chapters, near-black copy, tiny folio numbers, graphic rules and minimal printed-seal details. Typography: Anton or Barlow Condensed Black for oversized headlines, DM Mono for captions, DM Sans for paragraphs, one selective italic serif for editorial emphasis. Prioritize typographic hierarchy and clean whitespace over clutter. Preserve bright aluminum reflections and cold condensation from the supplied product art.

## Reference-inspired sequence
Reproduce **the choreography, not the original brand**: (A) hero product over massive type; (B) product shifts to expose a technical panel; (C) giant editorial `MOUTHFEELS`-style moment translated into unique REVEL wording; (D) red/black irregular splash labels for flavor notes; (E) designed product story/collection finale. The source shows a bottle; replace it with the REVEL can. Add a sophisticated REVEL color interlude and final CTA. If only one product visual is supplied, never fabricate additional SKUs or pretend to show a verified reverse-angle photo.

## Motion system — high priority
- One single normalized vertical scroll timeline controls the entire experience; a sticky viewport canvas persists across scene changes.
- Implement GSAP ScrollTrigger + Lenis with correct synchronization, or justify a stable unified custom RAF loop. Prevent competing scroll interpolation systems and clean up all listeners on unmount.
- Move the **same** can throughout the entire story. Keyframe x/y translation, `rotateZ`, subtle scale and optional small parallax with gentle easing. Start approximately 10° tilted, pass through a more upright detail-reading pose, then finish nearly centered; values must be configurable and refined by visual testing.
- Text reveals: clipped display text, line-by-line editorial staggering, subtle spread-to-settle tracking; info cards with ruled wipes, restrained image masks and splashes with staggered emergence; scene colors transition cleanly without abrupt flashes.
- All effects derive deterministically from scroll progress. Reverse-scrolling must unwind them naturally, without reset pops, blank frames or cumulative transforms. Add a robust progress indicator (desktop vertical/mobile horizontal), chapter jumps and smooth back-to-top.
- Avoid arbitrary giant rotations, warp/distorted labels, scroll hijack, perpetual noisy particle systems, excessive bloom, forced snapping, autoplay sound and FPS-dependent time-based animation.

## Product rendering truthfulness
**Mandatory baseline:** animate the supplied product PNG as premium 2.5D. This asset has only a front-perspective view. No full 360-degree rotating can, true back label or faithful unseen faces can be derived from it. If a GLB or complete label artwork is supplied later, create a separate optional R3F/WebGL renderer with actual can geometry, PBR metal, faithful texture wrapping, studio lighting, physically plausible specular reflection and real camera orbit. The fallback must remain visually excellent on mobile.

## Suggested chapters
1. **THE OPENING:** `A LITTLE LOUDER.` Floating can, hero typographic stack, stamp and short scroll cue.
2. **MEET THE CAN:** `MEET THE RED BERRY.` Product shifts right; authentic original can and intro copy are legible.
3. **THE DETAILS:** `355 ML OF ATTITUDE.` Crisp technical card and only label-supported facts.
4. **THE FEELING:** `THE GOOD KIND OF FIZZ.` Monumental distressed display typography, editorial inset and product parallax.
5. **THE FLAVOUR:** `BRIGHT. BERRY. BOLD.` SVG ink splash flavor labels, gentle composition shifts, precise small text.
6. **THE COLOURS:** `FOUR SHADES. ONE FEELING.` Interlude with the four locked color values.
7. **THE FINALE:** `MAKE IT A REVEL MOMENT.` Can returns front-dominant; CTA and smooth replay.

Use this chapter plan as an editable proposal, not an instruction to add redundant sections. Let the actual attached recording guide the final visual pacing. Keep creative text original. The rendered can may include claims such as “zero sugar”; do not independently add unsourced nutritional, ingredient, origin or certification claims in site copy.

## Technical quality requirements
- Stack: existing Next.js App Router + React + TypeScript; GSAP ScrollTrigger + Lenis where beneficial; optional R3F only if using true 3D mesh. All animation logic must be cleanly modular.
- Responsive: design and manually verify 320px, 390px, 768px, 1440px, 1920px. Mobile is a first-class composition, not a scaled desktop screenshot. Respect safe areas and readable line breaks.
- Performance: prefetch the hero image, optimize secondary media, animate transform/opacity, prevent layout shift, prefer lightweight SVG splashes over heavy WebGL simulation; profile critical scroll stages. Aim for visually smooth 60fps on suitable desktop hardware with sensible mobile fallback.
- Accessibility: semantic HTML, functioning keyboard/menu interaction, alt text, readable contrast, visible focus, reduced-motion adaptation, no blank page without JS where possible.
- Motion polish: product optical-center stability; no text hiding beneath the can when essential; realistic shadow that moves with it; layered typography; consistency in scene lighting and scale; no clipped image edge on mobile.

## Required deliverables
1. **Short reference audit**: enumerate what was visibly observed in the initial showcase, with screenshots/time markers where possible; separate observations from assumptions.
2. **Complete implementation**: working updated Next.js source with organized components, config-driven scene data and reusable motion helpers.
3. **Standalone preview** or static export when feasible, and clear local run commands.
4. **Verified QA evidence**: screenshots of every chapter at desktop and mobile, smooth forward/reverse test results, menu/navigation tests, reduced-motion tests, browser console/error check and actual build results.
5. **Performance report**: key costs, optimizations and anything not measured.
6. **Asset list**: exact used files, missing assets for true 3D or lifestyle photography, and which extras were designed as placeholders.
7. **Change log**: what was kept from existing site, what changed and why. Do not claim success or test coverage without actually running checks.

## Acceptance criteria
The product looks exactly like the supplied REVEL artwork; the design unmistakably evokes the source's cream/red large-type editorial product drama without copying its branding; scroll control is smooth, continuous and reversible; each section has a distinct intentional composition and transition; mobile works with no collisions; visual contrast and text remain readable; nav/progress/CTA work; and source code is buildable and easy to revise.

## Execution order
1. Inspect all attachments and confirm available assets.
2. Audit current code and visually compare screenshots with key reference frames.
3. Implement the motion/scene engine first, preserving existing routes and behavior.
4. Improve typography/layout, custom graphics, crossfade/mask timing and product shadow.
5. Tune each scene on desktop and mobile; test both scroll directions.
6. Run the build and browser QA. Fix what fails.
7. Deliver working files, screenshots, concise change log and honest limitations.

**Do the work directly using available files/tools; do not stop at an outline or only a prompt. If an asset or interface prevents a feature, implement the highest-quality feasible fallback and identify the limitation.**

# END MASTER BUILD PROMPT
