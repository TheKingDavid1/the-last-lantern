# Prompts for ChatGPT Image Generation — Logo & Thumbnails
(Generate these in ChatGPT, then send the image files back to me — I'll add branded text/logo overlay and integrate into the pipeline.)

---

## 1. NEW LOGO PROMPT (one-off, replaces current logo)

```
A minimalist circular emblem logo for a YouTube channel called "The Last Lantern," a calm narrated true-story channel about mysteries, forgotten history, and abandoned places. Center: a single vintage oil lantern with a warm glowing amber flame, rendered in fine etched line-art / engraving style. Background: deep midnight navy blue with faint wisps of fog. Thin elegant circular border in warm gold. High contrast between warm amber glow and cool dark blue. No text anywhere in the image. Clean flat vector illustration style, must read clearly as a small YouTube channel avatar (simple enough to recognize at 48x48 px). Square canvas, 1:1 aspect ratio.
```

If you want a genuinely different direction instead of a refined version of the current one, tell me and I'll write an alternate concept (e.g., a compass instead of a lantern, a raven, an open pocket watch, etc.) — but keeping *some* consistent mark matters, since this same icon needs to appear across every thumbnail/intro/outro for brand recognition.

---

## 2. REUSABLE THUMBNAIL PROMPT TEMPLATE (use for every future episode)

Fill in the bracketed parts per episode, generate with **no text in the image** — I add the title text and logo watermark afterward for guaranteed-correct spelling and consistent branding.

```
A cinematic, high-contrast YouTube thumbnail background image, 16:9, no text anywhere in the image. Subject: [SPECIFIC SCENE — e.g. "the interior of an abandoned ballroom half-filled with drifting desert sand, dramatic light beams through broken windows"]. Mood: [eerie / melancholic / mysterious — match the episode's tone]. Color palette: warm amber/gold light against deep navy or charcoal shadow, strong contrast for small-screen visibility. Composition: subject positioned off-center (rule of thirds), clear open negative space in the [top OR bottom OR one side] third for title text overlay. Style: painterly digital illustration, dramatic and slightly dark, but not gory or graphic. High detail, sharp focus on the main subject.
```

**Filled example for Episode 1 (Kolmanskop) — already done, but here's the same template applied:**
```
A cinematic, high-contrast YouTube thumbnail background image, 16:9, no text anywhere in the image. Subject: the interior of a grand abandoned ballroom, ornate ceiling, dramatic light beams through tall arched windows, the floor filled knee-deep with rippling desert sand dunes. Mood: eerie, melancholic, quietly grand. Color palette: warm amber/gold light against deep shadow, strong contrast for small-screen visibility. Composition: subject centered with clear open negative space in the bottom third for title text overlay. Style: painterly digital illustration, dramatic and slightly dark, but not gory or graphic. High detail, sharp focus.
```

### Current best-practice hooks for this niche (bake into whatever specific scene you pick):
- **3-5 word punchy title max**, active voice, concrete stakes ("THE DESERT ATE THIS TOWN" not "A Story About a Ghost Town")
- **One dominant visual subject**, not a busy collage — cluttered thumbnails lose in small-screen feeds
- **Warm/cool color contrast** (amber light vs. cool shadow) reads as "premium" and pops against YouTube's white/dark UI
- **Leave clear negative space** for text — don't make me composite text over a busy area
- **Accuracy matters** — whatever hook the thumbnail promises, the video must actually deliver (this is also a monetization-policy guardrail, not just an ethics one)
