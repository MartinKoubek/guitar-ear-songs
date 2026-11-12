# Song library guide
- Public content repository for Guitar Ear. Only `assets/` is bundled in the Android APK.
- Current reference: eight Hot Cross Buns lessons, documented in REFERENCE.md; FORMAT.md describes the schema.
- Preserve stable IDs and catalog order. Text is English-only; use B and sharp names.
- Edit catalog and note JSON together; retain two explicit empty count-in bars and independent learner/backing parts.
- Validate through the parent Android project's JDK17 unit/lint/build checks. Push content changes before updating the parent submodule pointer.
- Keep keys, credentials, recordings, device evidence and legacy test songs out of this public repository. Never add commit co-authors automatically.

- Organized catalog v2: read LIBRARY.md before adding content. catalog.json orders compositions within levels; each song.json orders lessons and supplies one optional cover. Preserve all IDs. Missing artwork uses default-cover.webp, then the bundled app fallback. V2 requires an updated app.

- Quiet Morning: eight original Level1 picking lessons after Hot Cross Buns, 3/4 at40BPM, only frets0-3. See QUIET-MORNING.md. No cover field uses the shared default. Amazing Grace adds four follow-up Level1 accompaniment lessons (AMAZING-GRACE.md); total35 lessons. Existing23 lesson files remain unchanged.


- Optional `lyrics` is documented in FORMAT.md; LYRICS.md maps all35 lessons. HCB03-08, all Mary lessons, Twinkle02-10 and Amazing Grace04 have timed words (21 lessons,206 line occurrences). Preserve Mary's inside-bar Its pickup and sung word durations across Twinkle fills. Quiet Morning stays instrumental. Amazing Grace04 uses a verified independent sixteen-bar vocal map: one explicit guitar-rest pickup bar after count-in, then the existing rest bar for round2; me/see hold five beats. Preserve note/backing data; lyric display requires the updated APK and older parsers ignore the field.
