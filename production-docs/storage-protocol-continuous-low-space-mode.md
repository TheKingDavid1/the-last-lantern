# The Last Lantern — Permanent Storage Protocol Amendment: Continuous Low-Space Mode

*Adopted as the default workspace-management strategy for every future episode, superseding earlier ad-hoc versions of this rule. This is now how I work by default, not an exception.*

## Default operating principle
The local workspace is **temporary RAM-like production space**. GitHub is **persistent storage**. Never fill the workspace just because capacity technically remains — keep it lean, archive progressively, delete verified intermediates aggressively, preserve headroom for the next operation.

## 1. Work in small stages
`GENERATE → VERIFY → ARCHIVE → DELETE → CONTINUE` for every production batch — never generate a whole episode's intermediates simultaneously.

## 2. Maintain a real safety buffer
128MB is a hard ceiling, not usable capacity. If usage approaches the threshold: stop generating → identify disposables → verify GitHub copies exist → delete verified disposables → recheck space → only then continue.

## 3. Archive immediately, not at stage-end
The moment a file becomes a verified production asset: push to GitHub → verify the remote copy is readable → only then remove local duplicates.

## 4. File classification (never delete the only copy of KEEP items)
- **KEEP:** final narration, final script, final scene manifest, final alignment data, approved source/Flow images, final assembled video, permanent outro/CTA assets, anything required for recovery
- **REGENERABLE (delete after archive/verification):** TTS chunks post-concatenation, raw alignment intermediates post-final-alignment, temp transcription files, temp extracted frames, failed generations, duplicates, conversion intermediates, temp renders, caches, debug logs

## 5. Prevent peak storage, not just final totals
Calculate the likely *temporary peak* before expensive operations (e.g. 10 images at once) — if the peak would be unsafe, batch it (2–3 at a time, archive + clean each batch, continue), even if the final total would technically fit.

## 6. Recovery-first design
Every meaningful stage ends with: `VERIFY → PUSH → VERIFY REMOTE → CLEAN LOCAL`. A session ending unexpectedly should always be resumable from the latest GitHub checkpoint, never requiring a full rebuild.

## 7. Session-start check (every new session)
Inspect local workspace usage → inspect the GitHub episode archive → determine what already exists remotely → download only what's needed for the current stage → never restore a whole episode locally just because it's available.

## 8. Session-end check (before ending)
Push required assets → verify remotely → remove disposable locals → report current workspace usage, latest recovery checkpoint, and exactly what remains locally.

## 9. Critical rule: a snapshot warning is not proof of data loss
When a platform storage warning appears, **immediately verify against the actual GitHub archive** rather than assuming the worst. Only treat something as actually lost if it's genuinely missing from GitHub after a direct check. (Precedent: Aug 11 Joyita session — a workspace-over-budget warning triggered a full GitHub verification; all 15 files were confirmed present and byte-intact. Nothing was actually lost — the dropped local files were disposable intermediates already superseded by verified archives.)
