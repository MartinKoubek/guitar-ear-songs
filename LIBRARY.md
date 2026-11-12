# Ordered song library and artwork

The Android application supports catalog v1 (legacy flat library) and v2 (organized compositions). Deploy the v2-capable app before publishing this catalog: older apps will reject it and retain their previous offline library.

## Layout

```
assets/songs/
  catalog.json
  default-cover.webp
  level-01/hot-cross-buns/
    song.json
    cover.webp
    lessons/<stable-lesson-id>.json
```

`catalog.json` has `schemaVersion: 2`, `levelCount`, optional `defaultCover` (relative to `songs/`) and ordered `levels`. Each level has `number`, `title`, `description` and an ordered `songs` array of manifest paths relative to `songs/`.

Example level:
```json
{"number":1,"title":"First Notes & Rhythm","description":"Your first melody.","songs":["level-01/hot-cross-buns/song.json"]}
```

Each `song.json` has stable composition `id`, `title`, `description`, optional `cover`, and ordered `lessons`. Cover and lesson paths are relative to the composition folder. Each lesson entry has stable `id`, `title`, `description`, `asset`, and optionally `section`. The actual lesson JSON and its schemaVersion are unchanged.

```json
{
  "id":"example-song",
  "title":"Example Song",
  "description":"Learn a familiar melody.",
  "cover":"cover.webp",
  "lessons":[
    {"id":"example-melody","title":"Example Song - Melody","description":"Start with the tune.","asset":"lessons/01-melody.json"}
  ]
}
```

Move array entries to reorder compositions or lessons. Filenames do not control display order. Preserve existing lesson IDs when renaming titles, moving files or replacing images: progress/history use IDs. Level numbers remain the app's numbered progression.

## Images

Use a landscape WebP, ideally 960 pixels wide. PNG and JPEG are also supported. Each composition has one cover for all its lessons. The existing guitar, lamb and night-sky illustrations are the approved original Plucksy artwork, copied from the app; no external copyrighted photos are needed. `default-cover.webp` is the existing universal guitar illustration. Welcome art remains an app resource.

To add an image later, add `cover.webp` in the composition directory and set `cover` in `song.json`. Replace the file to update it. Images participate in the revision digest, so image-only updates are recognized. No APK update is needed after this feature is installed.

A missing cover reference or file falls back to the downloaded default cover. Invalid image data or unsupported dimensions also falls back. If the default is absent or invalid, the app uses its bundled guitar illustration. Only referenced images are kept. Decode happens off the UI thread and is bounded to 1024 pixels on the longest side; source dimensions must be at most 4096 per side. Image files are limited to 2 MiB, JSON files to 1 MiB, downloads to 20 MiB and total expanded archives to 64 MiB. Oversized archives are rejected without changing the active library.

## Installation and validation

Update Songs downloads the complete GitHub ZIP, validates all required manifests and lessons, then atomically activates one immutable revision. Missing optional pictures do not block music. No remote URLs, absolute paths or parent-directory references are allowed in manifests. Existing downloaded v1 libraries remain readable.

The current migration preserves all 23 score files byte for byte and all composition/lesson IDs. Tests cover the real archive installer, ordering, unsafe references, missing pictures, image-only changes, offline reopen and Android decoding/fallback. The existing tests continue to check the full curriculum, scoring, PDF and Home selection.

Publish the song submodule first, then record its commit in the app repository. Keep changes local until publication is requested.
