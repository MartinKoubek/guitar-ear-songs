# Song library guide
- Public content repository for Guitar Ear. Only `assets/` is bundled in the Android APK.
- Current reference: eight Hot Cross Buns lessons, documented in REFERENCE.md; FORMAT.md describes the schema.
- Preserve stable IDs and catalog order. Text is English-only; use B and sharp names.
- Edit catalog and note JSON together; retain two explicit empty count-in bars and independent learner/backing parts.
- Validate through the parent Android project's JDK17 unit/lint/build checks. Push content changes before updating the parent submodule pointer.
- Keep keys, credentials, recordings, device evidence and legacy test songs out of this public repository. Never add commit co-authors automatically.
