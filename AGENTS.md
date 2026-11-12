# Song library guide
- Public content repository for Guitar Ear. Only `assets/` is bundled in the Android APK.
- Current reference: eight Hot Cross Buns lessons, documented in REFERENCE.md; FORMAT.md describes the schema.
- Preserve stable IDs and catalog order. Text is English-only; use B and sharp names.
- Edit catalog and note JSON together; retain two explicit empty count-in bars and independent learner/backing parts.
- Validate through the parent Android project's JDK17 unit/lint/build checks. Push content changes before updating the parent submodule pointer.
- Keep keys, credentials, recordings, device evidence and legacy test songs out of this public repository. Never add commit co-authors automatically.

- Organized catalog v2: read LIBRARY.md before adding content. catalog.json orders compositions within levels; each song.json orders lessons and supplies one optional cover. Preserve all IDs. Missing artwork uses default-cover.webp, then the bundled app fallback. V2 requires an updated app.

- Quiet Morning: eight original Level1 picking lessons after Hot Cross Buns, 3/4 at40BPM, only frets0-3. See QUIET-MORNING.md. No cover field uses the shared default. Amazing Grace adds four follow-up Level1 accompaniment lessons (AMAZING-GRACE.md); total35 lessons. Existing23 lesson files remain unchanged.

- Optional `lyrics` is documented in FORMAT.md. Timed Hot Cross Buns lessons03-08 have traditional words aligned to actual melodic phrases; lessons01-02 remain rhythm/target preparation without lyrics. Preserve note/backing data when editing text. Updated APK required for display; older parsers ignore the optional field.
