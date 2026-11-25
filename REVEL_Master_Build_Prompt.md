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

