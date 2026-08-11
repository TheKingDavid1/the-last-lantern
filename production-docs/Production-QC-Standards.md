# The Last Lantern — Production QC Standards

*Save this file in the agent workspace and reference it at the start of every session and before marking any episode QC-complete. Update it whenever a new mistake pattern is caught — this doc should grow over time, not stay static.*

## How to use this
- At the start of a session: "Read Production QC Standards before continuing work."
- Before finalizing any episode: "Run the Pre-Upload Checklist against this episode before marking it QC-complete."
- When a new issue is caught (by me, another model, or you), it gets added to the relevant section immediately, in the same format as existing entries.
- **Every "Origin" note must be independently verified before being written down as fact** (see Rule 0). An "Origin" note is a permanent precedent future sessions will trust — it must describe something that was actually confirmed against the real file, not something a review tool claimed.

---

## RULE 0 — Verify before recording (the rule that governs all other rules)
No issue gets written into this document as an "Origin" until it's been checked against the actual file — real extracted frames at the cited timestamp, real audio-level measurements, or a direct logical check against what the pipeline can actually produce. A review tool's claim is a lead to investigate, not a fact to record.

*Origin: Episode 1 — a review claimed hallmark AI-video-generation artifacts (warping, frame-to-frame lighting drift) in a video that contains zero AI-generated video clips (100% static images with deterministic zoom/pan). Direct frame extraction and audio-level measurement showed 3 of 6 flagged issues were not present in the actual published file. Applying "fixes" for them would have wasted effort chasing phantom problems and, in one case, pointed toward a completely wrong technical remedy (re-seeding "generated" content that was never generated).*

## RULE 1 — Hook timing
The core stakes/anomaly must be stated in the **first 3–5 seconds**, not built up to through scene-setting or poetic wind-down. Reflective/atmospheric material is welcome, but it goes *after* the hook line lands, never before it.

*Origin: Episode 1 (Kolmanskop) hook payoff didn't land until ~0:12 — confirmed via direct frame inspection. Fixed in v4: stakes now land within ~5 seconds of content start.* ✅ **Verified and corrected.**

## RULE 2 — Motion-clip sourcing
Every AI-generated motion clip must be **image-to-video from an already-approved, locked still** — never blind text-to-video for anything that will appear in the final cut. The still anchors composition and lighting, which is what prevents warping/morphing artifacts.

*Origin: precautionary rule for future motion-clip work (Google Flow integration) — not yet used in Episode 1, which contains no generated motion clips at all. Sound practice regardless.*

## RULE 3 — Mandatory frame-by-frame artifact check
Before any generated clip is approved for the final cut, review it at **minimum 3 timestamps** (start, middle, end) specifically checking for: warping/morphing in fine detail, lighting or shadow-direction shifts between frames, and unnatural edges where generated motion meets a static element.

If any artifact is found: do not attempt to mask it in editing. Either regenerate from a different seed/attempt, swap in a different approved still, or replace with a static crop that excludes the affected area.

*Origin corrected: the specific claims of "sand-ripple warping at 1:42" and "lighting flicker at 2:50" in Episode 1 were checked directly against the published file — frames pulled at both timestamps (and neighboring frames) showed a static map/desk shot with no sand present at all at 1:42, and an unchanged, non-flickering light beam at 2:50. Neither artifact exists in Episode 1, which has no generated video content to have produced them. **This rule is retained as sound forward-looking practice for when we actually start using Google Flow — not because it caught a real issue in Episode 1.***

## RULE 4 — Motion clip budget and placement
Maximum 2–3 AI-generated motion clips per episode. Reserve them exclusively for the cold-open hook shot and the emotional climax. Never spend a generation slot on establishing/overview material — those stay as static pans.

*Origin: general best practice for managing artifact risk as motion-clip usage increases (see qa-and-motion-clip-protocol.md for the fuller Flow workflow and its real constraints — Flow-style tools generate short ~4-8s clips, which limits which segments they can realistically replace).*

## RULE 5 — Pacing on early shots — ⚠️ needs your input, conflicts with verified research
As originally written, this rule called for shortening any early shot over ~12-15 seconds. **I'd push back on this as written**: our own verified competitive research (LEMMiNO, Amy's Crypt, Bedtime Stories, Wendigoon) confirms calm, unhurried pacing is a *strength* in this specific niche, not a flaw — cutting it to chase generic "momentum" would work against the calm/premium brand these episodes are built on.

**Revised version:** early shots can and should hold as long as the calm pace calls for — but if a held shot has *zero* visual variation for its full duration (same static crop, no pan/zoom at all), add a very subtle secondary movement so it doesn't read as a frozen frame. This is about avoiding literal stillness, not about speeding up the pace.

*Origin corrected: the specific claim ("0:34–0:48 machinery shot dragged") wasn't independently re-verified against the actual file before this doc was drafted. Keeping a softened version of the rule since "avoid a fully frozen frame" is reasonable regardless of the original claim's accuracy.*

## RULE 6 — Duration matching on generated-clip swaps
When a generated motion clip replaces a static-pan segment, its duration must be trimmed/matched exactly to the segment it replaces before merging. After any such swap, manually re-check caption sync from that point forward — never assume it carries over automatically.

*Origin: identified as a structural risk when planning future motion-clip integration (Google Flow workflow) — a real engineering concern independent of whether any specific past example was accurate.*

## RULE 7 — Audio ducking under narration
Ambient/atmospheric audio beds should be ducked 3–4dB under narration, or EQ-cut in the 1–4kHz range, in any section with extended overlap (5+ seconds).

*Origin corrected: the specific claim ("1:05–1:12 wind/sand layer crowded vocal clarity") was checked with direct audio-level measurement — that window measured -21.3dB vs. -20.6dB for the whole track, no meaningful difference, no masking event present. **Retained as sound general audio-mixing practice for future episodes, not because Episode 1 actually had this problem.***

## RULE 8 — Dark-gradient banding
Before final export, check dark/low-light interior shots for gradient banding. If present, apply a subtle 2–3% noise/grain overlay to break it up. Export from the highest-quality available source — never re-compress an already-compressed intermediate file for final upload.

*Origin: not independently confirmed present in Episode 1 (could not be definitively verified either way from frame inspection). Applied preventatively in v4 regardless, since there's no downside to a subtle grain pass.*

## RULE 9 — Branding animation
Subscribe/bell motion graphics are allowed genuine pulsing/shaking motion (not restricted to fades/slides only) — this is a deliberate, requested feature, not an oversight.

*Origin corrected: the original claim that Episode 1 was "confirmed correctly restrained on actual review" doesn't hold up — this feature was explicitly requested (the subscribe button motion was a direct ask), built, and verified with extracted frames showing genuine pulsing/shaking between frames seconds apart. A review method that samples individual frames can't perceive inter-frame motion the way a human watching in real time can, so "looked restrained" in that kind of review isn't evidence the motion is absent — it's a known limitation of frame-sampling review. Decision (pending override): keep the current motion as-is. If a future review independently confirms the motion is genuinely too distracting when watched in real time (not frame-sampled), revisit — but the bar is an actual real-time viewing complaint, not another frame-sampled review.*

---

## Pre-Upload Checklist (run against every episode before marking QC-complete)
- [ ] Hook payoff lands within 3–5 seconds
- [ ] Every generated motion clip is image-to-video from an approved still (Rule 2)
- [ ] Every generated motion clip checked at start/middle/end for artifacts (Rule 3)
- [ ] No more than 2–3 motion clips total, placed only at hook/climax (Rule 4)
- [ ] Early shots avoid being fully frozen (no pan/zoom at all) for their full duration (Rule 5, revised — calm long holds are fine and encouraged per our niche research, as long as there's some subtle continuous movement)
- [ ] Any clip-swap duration matched exactly, captions re-checked after (Rule 6)
- [ ] Narration audible against ambient bed everywhere they overlap (Rule 7)
- [ ] Dark interiors checked for banding (Rule 8)
- [ ] Outro/branding motion matches Rule 9 (pulsing/shaking subscribe+bell is allowed and current)
- [ ] Palette matches the assigned pillar color throughout (see thumbnail-style-guide.md)
- [ ] Script has genuine narrative variance from the previous 2 episodes, not a reused skeleton
- [ ] Every "Origin" note added this episode has been independently verified per Rule 0 before being written down
