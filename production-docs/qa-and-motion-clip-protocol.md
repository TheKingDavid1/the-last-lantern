# The Last Lantern — Quality Assurance & Motion-Clip Integration Protocol

## Part 1: Verification rule (why this exists)
On Episode 1 alone, we caught two real external-review errors before acting on them:
1. Claude's research described a hook technique ("start with the end") that turned out to be a mischaracterization of MrBallen's actual quoted technique — verified against his real interviews.
2. Gemini's review flagged "AI artifact warping," "lighting flicker," and "audio masking" at specific timestamps — verified against the actual published file (real frames pulled directly from the file, real audio-level measurements) and none of the three were present. The video contains zero AI-generated video clips (only static images with deterministic zoom/pan), so those specific artifact types aren't even mechanically possible in it.

**Standing rule: no fix gets applied based on an external AI review (Claude, Gemini, or any other model) until it's checked against the actual file — real extracted frames at the cited timestamp, real audio-level data, or a plain logical check against what our pipeline can actually produce.** A review claim is a lead to investigate, not a verified fact. This isn't about distrusting the tools — it's that any model reviewing video/audio without frame-perfect tooling can produce fluent, specific-sounding, wrong descriptions, and "specific and confident" isn't the same as "true."

**Practical checklist before applying any external review's fix:**
- [ ] Pull the actual current file (not a description of it) — from GitHub Release if not sitting locally
- [ ] Extract real frames at the cited timestamp(s), plus 2-3 seconds before/after to check for actual change over time
- [ ] For audio claims, run `volumedetect` (or equivalent) on the cited window vs. a comparison window — don't rely on ear/description alone
- [ ] Cross-check any claim that references a technique/technology/framework we haven't ourselves discussed or built (ask before assuming it's real)
- [ ] Only then decide: apply as-is, apply with modification, or discard

## Part 2: Motion-clip integration workflow (Google Flow)

**The idea (confirmed with you):** the current pipeline generates the full video as usual (stills + narration + captions). Separately, a small number of specific images get selected and animated in Google Flow (Google's Veo-based image-to-video tool) by you, since I can't access it myself. You bring the resulting clip(s) back here, and I integrate them — swapping the corresponding still-image segment for the real motion clip — without breaking caption or voice sync.

### What's genuinely feasible on my end
- **Receiving and integrating a finished clip is straightforward.** Our pipeline is modular — each visual "segment" is an independent chunk in a sequence. I can substitute any segment's static-image-plus-pan for a real video clip you provide.
- **Duration-matching is the actual safeguard against sync drift** (this part of Gemini's feedback was structurally correct even though the specific example wasn't). I will trim/conform any clip you provide to the exact duration of the segment it's replacing before splicing it in — captions are timed against the audio track, which never changes, so as long as the replacement clip's duration matches exactly, nothing downstream shifts.
- **I'll visually QC every clip before integrating it** — extracting frames and actually looking for warping/inconsistency, the same verification standard from Part 1, applied prospectively this time instead of retroactively.

### Major downsides / feasibility limits — read before relying on this
1. **I cannot access Google Flow myself.** No browser, no API credential for it in this sandbox. The generation step is 100% on your end; I only receive and integrate. This isn't a workaround-able limitation — treat it as a fixed hand-off point in the workflow, not something I can eventually automate away.
2. **Duration mismatch is the biggest structural risk.** Tools like Flow (Veo-based) typically generate short, fixed-length clips — commonly in the 4-8 second range per generation, not arbitrary custom durations. Our segments range from ~7 seconds to over a minute. A generated clip almost certainly won't be long enough to replace an entire long static hold outright. Realistic approach: use the motion clip for the *first* several seconds of a moment, then let it settle back into a still with the normal pan for the remainder — not a full 1:1 swap for our longer segments.
3. **I can't verify Google's current credits/pricing for Flow.** Any specific number (e.g. "50 daily credits") isn't something I can confirm from here — check Google's current terms directly rather than trusting a number from any AI review, mine included.
4. **This is a manual, multi-turn workflow, not an automated pipeline.** You generate in Flow → upload the clip here → I integrate and re-verify sync → repeat. Expect iteration, not one-shot automation.
5. **Reserve for climax/hook moments only.** This part of the original suggestion is good practice independent of anything else: 2-3 motion shots per episode at genuine high-impact moments (per our episode structure's "climax" beat), not a general upgrade pass. More motion clips = more surface area for visual inconsistency, so spend them where they earn their cost.
6. **Anchor on our own locked stills (image-to-video, not blind text-to-video).** This is the right call you already made — it keeps composition/lighting anchored to something already approved, which is the main defense against a generated clip drifting away from the rest of the episode's visual identity.

### Recommended process once you bring a clip back
1. You tell me which segment/moment it's replacing (by timestamp or description).
2. I check the clip's actual duration against that segment's planned duration.
3. I extract frames from the clip and visually inspect for artifacts before integrating — flag anything that looks off rather than assuming it's fine.
4. I trim/conform duration, splice it in, rebuild only what's needed (not necessarily the whole video from scratch if the change is isolated), and re-verify caption sync in that section specifically.
5. Push, verify against GitHub directly, report back with the specific before/after.
