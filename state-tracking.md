# The Last Lantern — State Tracking
_Last updated: Week 1, Day 1_

## Locked decisions
- **Channel name:** The Last Lantern
- **Narrator persona:** The Keeper (anonymous-but-consistent, free TTS voice, locked as `voice-00`)
- **Story #1 topic:** Abandoned place — Kolmanskop, Namibia
- **Channel hosting decision:** Brand new channel — NOT reusing the dormant history channel or ViralSatisfyingHub, to avoid content-mismatch/algorithm confusion
- **Episode 1 title:** "Kolmanskop: The Diamond Ghost Town the Desert Swallowed Whole (True Story)"
- **Episode 1 thumbnail:** `content/thumbnails/thumb_A_ballroom.jpg` ("THE DESERT ATE THIS TOWN") — chosen over thumb_B because B's original copy ("Abandoned in One Week") was factually inaccurate against the fact-checked script
- **Upload strategy:** Shorts-first channel warm-up (2 shorts before long-form launch), then weekly rhythm anchored Fri/Sat 8-10PM WAT (hits UK evening prime + lands ~3-5PM US Eastern, ahead of US evening peak)
- **Monetization path emphasis:** Shorts-views threshold prioritized over long-form watch-hours threshold as the faster realistic route (see `content/upload-growth-rpm-guide.md`)

## Setup checklist status
- [x] Channel name locked
- [x] Logo generated (`branding/logo.png`)
- [x] Banner generated (`branding/banner.png`)
- [x] Channel description drafted (`channel/channel-description.md`)
- [x] Persona locked (`channel/persona.md`)
- [ ] YouTube channel actually created (manual — you)
- [ ] 2-Step Verification enabled (manual — you)
- [ ] AdSense account started (manual — you)
- [ ] Handle secured (manual — you)
- [ ] Upload defaults reviewed: Not Made for Kids + synthetic disclosure toggle (manual — you)
- [ ] Licensing check table filled in for chosen TTS/image/music tools (manual — you, template in manual-setup-checklist.md)

## Content pipeline status
- [x] Story #1 topic selected — Kolmanskop, Namibia
- [x] Story #1 script drafted (`content/story-01-kolmanskop-script.md`)
- [x] Topic bank of 10 future stories drafted (`content/topic-bank-10.md`)
- [x] Fact-check pass on Story #1 script — logged in script file, 1 date discrepancy + 1 unverified anecdote both handled with honest on-camera hedging rather than false precision
- [~] Atmosphere/still asset library — 10 of 12 pieces generated in `assets/kolmanskop/` (ballroom, hospital, house exterior, coffee cup still life, bowling alley, garden, tram tracks, wide dunes, lantern windowsill, map/paper texture). Remaining 2 (hyena silhouette, casino chandelier) queued for next session due to per-session image generation cap.
- [x] Story #1 narration recorded (TTS) — Keeper voice locked as `voice-00`; 5 segments generated + stitched into `content/narration_audio/story-01-full-narration.mp3` (~7m07s raw)
- [x] Story #1 fully assembled in-house (no CapCut needed) — final video at `final_deliverables/TheLastLantern-Ep01-Kolmanskop.mp4`
  - Word-level caption alignment via faster-whisper + original-script forced alignment (95% direct match)
  - Animated word-pop captions (Anton font, amber keyword highlighting) burned in
  - Ken Burns pans/zooms across 10 atmosphere stills, scene-matched to script beats via keyword timestamp search
  - Procedurally-synthesized ambient bed (no licensing exposure) mixed under narration
  - Branded intro card + "subscribe" outro card
  - Final: 1920x1080, H.264/AAC, 7m17s, ~88MB
- [ ] 4 Shorts cut from this episode (hook list already in `content/story-01-kolmanskop-script.md`)
- [ ] Story #1 + first Short uploaded (manual — you, via manual-setup-checklist.md)

## Weekly output log
| Week | Long-form uploaded | Shorts uploaded | Asset session done | Notes |
|---|---|---|---|---|
| 1 | — | — | — | In progress |

## Threshold tracking (fill in once channel is live)
| Date | Subs | Watch hours (12mo) | Shorts views (90d) | Expanded tier hit? | Full YPP hit? |
|---|---|---|---|---|---|
| | | | | | |

## Policy/compliance log
| Date | Item checked | Result |
|---|---|---|
| Week 1 Day 1 | Persona/authorship fingerprint defined | Done |
| | | |

## Infrastructure log (GitHub + workspace discipline)
- **GitHub repo live:** github.com/TheKingDavid1/the-last-lantern (public) — canonical backup for all lightweight production files (scripts, persona, branding, assets, narration, captions, guides)
- **Episode videos** stored as GitHub Releases (not committed directly — too large for normal git), e.g. Episode 1: github.com/TheKingDavid1/the-last-lantern/releases/tag/episode-01-kolmanskop
- **Known platform quirk:** the sandbox does not persist `.git/` folders or credential files (`.git-credentials`) between turns — git must be re-initialized (`git init` + `remote add`) each time we push in a new turn. Cheap to redo, not a real problem, just a step to remember.
- **Incident (Aug 9, Turn ~15):** the 10-image Kolmanskop asset library was silently dropped from the workspace snapshot (over the 128MB budget at save time), and the local copy was deleted based on an unverified assumption it had already reached GitHub. It hadn't. Images were regenerated from the original prompts (saved in this repo under `production-docs/chatgpt-image-prompts.md`-adjacent notes) and re-pushed.
- **New rule going forward: verify a GitHub push against the API (list actual file contents / sizes) before deleting any local-only copy of a file.** Never assume a push succeeded just because the `git push` command returned success — confirm the specific files exist server-side first.
