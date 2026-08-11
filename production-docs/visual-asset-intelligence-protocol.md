# The Last Lantern — Visual Asset Intelligence, Auto-Regeneration & Animation Readiness Protocol

*Permanent amendment to the Arena Production Protocol. Does not replace the Gemini/Arena division of responsibility — Gemini owns story/research/script/hooks/retention; Arena (this agent) owns visual production, image generation, continuity, animation direction, feasibility, asset management, and final integration.*

## Core principle: NO GENERATED VISUAL IS APPROVED BY DEFAULT
Pipeline: `SCRIPT REQUIREMENT → SCENE VISUAL SPEC → IMAGE GENERATION → INDIVIDUAL VISUAL QC → AUTO PROMPT IMPROVEMENT → REGENERATION IF NEEDED → ANIMATION READINESS QC → SEQUENCE/CONTINUITY QC → ASSET LOCK → ANIMATION DIRECTOR PROMPT → FLOW → ANIMATION QC → FINAL ASSEMBLY`

## 1. Individual Visual Asset Audit (immediately after generation, not at Flow stage)
- **A. Script alignment** — does it depict what's narrated, correct objects, correct environment?
- **B. Scene purpose** — why does this exist (hook/evidence/environment/transition/emotional beat)? Would a generic image weaken the story?
- **C. Historical/physical plausibility** — correct period, vessel/object/architecture, tech, no anachronisms, no contradiction of the fact-locked package
- **D. Visual composition** — readable subject, clear focal point, supports intended camera movement, enough info for animation if applicable
- **E. Continuity vs. neighbors** — subject identity, ship/hull design, period, environment, geography, lighting/time of day, weather, color language, object count, scale
- **F. Animation readiness** (if to be animated) — can the intended movement work, objects clearly separated, no malformed geometry, no ambiguous mutation-prone objects, sufficient depth for believable motion

## 2. Automatic failure classification
- **CRITICAL** (blocks approval, forces regeneration): wrong historical object/vessel/location/era, contradicts narration, wrong object count, major continuity break, physical impossibility, unsafe to animate
- **MAJOR** (blocks approval): environmental mismatch, incorrect placement, lighting/period mismatch undermining purpose, animation likely to artifact
- **MINOR** (note, can fix in assembly): color inconsistency, small composition issue, minor atmospheric mismatch

## 3. Automatic regeneration loop
`DETECT → DIAGNOSE → IDENTIFY EXACT FAILURE → MODIFY PROMPT WITH EXPLICIT CORRECTIONS → REGENERATE → RE-INSPECT`. Never just report "this is wrong" — always rewrite the prompt with specific negative/positive constraints targeting the exact detected failure.

## 4. Regeneration limit
Max 3 automatic attempts per scene. After 3 failures: `STATUS = HUMAN REVIEW REQUIRED`, with an explanation of what keeps failing, why it matters, and the available alternative.

## 5. Visual Quality Score (guidance, not override authority)
Score /10 each: Script Alignment, Scene Purpose, Historical/Physical Accuracy, Continuity, Composition, Animation Readiness, Cinematic Quality.
**90%+ = APPROVED · 75-89% = IMPROVE/REGENERATE · <75% = REGENERATE.**
Hard-fail conditions (CRITICAL/MAJOR classification) override the numeric score — a beautiful image depicting the wrong object is still a failure.

## 6. Second pass — whole-episode sequence continuity
After all individual images pass, review the full sequence conceptually: "Would a viewer believe these belong to the same production?" Check subject identity, era, geography, lighting, color grade, environment, camera language, scale, realism, recurring objects, storytelling progression. A scene that passes individually can still fail the sequence test — fix before proceeding.

## 7. Animation prompts only after full asset lock
No Flow prompt is written until an image has passed Individual QC + Animation Readiness QC + Neighbor Continuity QC. Every Flow scene handoff includes: source image, narrative purpose, exact narration segment, target duration, motion intensity, camera movement, subject movement, environmental movement, lighting behavior, depth/parallax needs, starting/ending composition, transition requirements, what must stay unchanged, what must not be introduced, negative instructions, and the final copy-ready prompt — written around the actual approved image, never an idealized one.

## 8. Animation-to-video sync check (before writing any Flow prompt)
Inspect: previous scene, current source image, following scene, narration timing, emotional intensity, existing color/lighting, intended transition. Motion must serve narration and feel like a continuation of the video — never added just because the tool can generate motion.

## 9. Post-Flow animation QC
Check the returned clip against: source image + animation prompt + narration + previous scene + following scene, for subject identity preservation, no object mutation/incorrect counts/unwanted people/new objects/geometry distortion/lighting discontinuity/motion beyond spec/unrealistic motion, correct emotional intensity, correct transition behavior. If it fails, report the exact failure and recommend the minimum correction — never blindly accept.

## 10. Storage-aware visual QC (integrates with the Continuous Low-Space Mode protocol)
`GENERATE → INSPECT → REJECT/DELETE immediately if failed, OR → APPROVE → ARCHIVE TO GITHUB → VERIFY → keep only what's required locally.` Never accumulate failed images, duplicate renders, temp conversions, intermediate chunks, or redundant copies. Before deleting an approved asset: push → verify remote exists → verify not corrupted → only then delete local. Never delete the only copy of an important asset.

## 11. Continuous improvement (mandatory post-episode retro)
After every episode, record: which visual generations failed and why, which prompt corrections worked, which animation prompts produced good results, which Flow movements caused artifacts, which transitions felt unnatural, which visual patterns supported retention vs. became repetitive. A problem found late becomes a lesson applied earlier next time — animation problems inform image-generation QC; assembly problems inform animation QC; post-publish problems inform the whole pipeline.

## 12. Asset approval states (track explicitly, never skip)
`[GENERATED] → [QC IN PROGRESS] → [FAILED - REGENERATION REQUIRED] → [REGENERATED] → [APPROVED] → [ARCHIVED] → [ANIMATION READY] → [FLOW GENERATED] → [ANIMATION QC] → [FINAL APPROVED]`
`[GENERATED]` is never treated as `[APPROVED]`.

---

## Live incident log (protocol applied in practice)

### Joyita Episode — Scene 08b "Dawn Hull" — CRITICAL failure, caught pre-protocol-adoption
- **Detected:** during manual continuity audit (before this protocol formally existed) — image showed an 18th-century square-rigged sailing galleon instead of the established 1950s wooden motor vessel used in Scenes 01/04/08a.
- **Classification:** CRITICAL (wrong vessel identity/era, major continuity break, contradicts every other ship shot in the episode).
- **Status at detection:** [FAILED — REGENERATION REQUIRED]. Held out of production, not used as-is.
- **Regeneration action (live first application of Section 3):**
  - **Attempt 1:** Rewrote prompt with explicit constraints — "1950s South Pacific motor merchant vessel," "no square sails," "no bowsprit," "no 18th-century galleon architecture." Result: vessel identity corrected (motor vessel silhouette, single mast, wheelhouse, matches established hull) — but **new CRITICAL failure introduced**: hull displayed fabricated painted text "MV LORENA," directly contradicting the fact-locked package (vessel is the *Joyita*). Status: [FAILED — REGENERATION REQUIRED], attempt 1 of 3.
  - **Attempt 2:** Rewrote prompt again, adding explicit "no name, no letters, no numbers, no painted text or lettering anywhere on the ship" constraint. Result: PASS on vessel identity, no fabricated text, correct continuity (warm dawn lighting appropriately distinct from Scene 08a's cold moonlit palette, since this is the "aftermath at sunrise" beat). Status: [APPROVED] → archived to GitHub, replacing the failed original at `EPISODES/joyita/SOURCE/static_images/scene08b_dawn_hull.png`.
  - **Resolved in 2 of 3 allowed attempts.**
  - **Lesson recorded for future image generation (per Section 11):** image models will sometimes invent plausible-looking but fabricated identifying text (ship names, plaques, labels) on generated objects even when not requested. **New standing rule: any image prompt for a named real-world object (a specific ship, place, document) must proactively include an explicit "no name/text/lettering/markings" negative constraint from the first attempt, not just after a failure is observed** — this failure mode was foreseeable and should be prevented by default rather than caught reactively next time.
