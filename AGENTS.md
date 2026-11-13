# Plucksy song authoring guide

This file applies to the entire public `MartinKoubek/guitar-ear-songs` repository.
Only `assets/` is distributed to the Android app. Keep credentials, private recordings,
device evidence and legacy test fixtures out of this repository. Never add commit co-authors automatically.

## Read before authoring

- [REFERENCE.md](REFERENCE.md): Hot Cross Buns, the reference learning progression.
- [FORMAT.md](FORMAT.md): detailed score, backing, polyphony and lyrics contracts.
- [LIBRARY.md](LIBRARY.md): catalog, manifest, artwork and archive constraints.
- [LYRICS.md](LYRICS.md): existing lyric arrangements and timing decisions.
- [QUIET-MORNING.md](QUIET-MORNING.md) and [AMAZING-GRACE.md](AMAZING-GRACE.md): song-specific arrangements.

Some documents retain historical catalog counts, flat paths or manual Update Songs wording.
Use the actual `assets/songs/catalog.json` and referenced manifests for current inventory.
The current compatible app checks for library updates automatically on a new app session.
When format details conflict, verify the Android parser and tests before publishing.

## How to create a song and its lessons

1. Choose a short, memorable tune and a playable final arrangement. Record the melody's
   source and usage rights. A traditional melody does not grant permission to copy a
   modern arrangement, recording, illustration or translation.
2. Decide whether the course teaches solo melody/fingerstyle or chord accompaniment
   for singing. Keep these goals explicit; do not silently replace one with the other.
3. Write and audition the complete simple melody first. Check pitch, rhythm, phrases,
   repeated motifs and comfortable fingering. It must sound recognizable without backing.
4. Split the arrangement into lessons with **one main new skill per step**. A useful
   sequence is right-hand preparation, short melodic phrases, complete melody, separate
   bass, melody plus bass, then a second/third bass string or a new melodic string.
   Use only steps the actual song needs; eight lessons is not a universal requirement.
5. Preserve familiar pitches, rhythm and register between steps. Do not simultaneously
   introduce a new melody, hand position, bass pattern and faster tempo. Prefer easy
   low-fret shapes; verify stretches and transitions on a real guitar.
6. Repeat a new phrase several times with preparation rests, then join phrases into
   the whole tune. Use deliberate repetition, not random notes or duplicated filler.
7. Set a comfortable authored BPM. Adding coordination may justify slowing down.
   Level 1 starts simply but is not restricted to open strings throughout the course.
8. Give each lesson a short English title, description and actionable instructions.
   Use B, not Czech H, and consistent sharp names. Lyrics retain their authored language.
9. Keep the student's scored notes separate from accompaniment. Backing must support
   the piece, not substitute for the student's melody or expected bass.
10. Supply the composition artwork and validate music, metadata and the app presentation
    together before publishing. Record song-specific decisions in its own Markdown guide.

## Directory layout and ordering

```text
assets/songs/
  catalog.json
  default-cover.webp
  level-01/example-song/
    song.json
    cover.webp
    lessons/
      01-melody.json
      02-first-bass.json
```

One composition has one `song.json` manifest and one shared cover. Each lesson has
its own score JSON. A lesson number is not a level number.

The catalog uses schema version 2. Paths below are relative to `assets/songs/`:

```json
{
  "schemaVersion": 2,
  "levelCount": 15,
  "defaultCover": "default-cover.webp",
  "levels": [
    {
      "number": 1,
      "title": "First Notes & Rhythm",
      "description": "Your first melody, one small step at a time.",
      "songs": ["level-01/example-song/song.json"]
    }
  ]
}
```

Add entries to the existing catalog, never replace it with this illustrative example.
The `songs` array orders composition cards within a level. In `song.json`, the
`lessons` array orders the learning steps. Filenames do not determine app order.

```json
{
  "id": "example-song",
  "title": "Example Song",
  "description": "Build a simple fingerstyle tune.",
  "cover": "cover.webp",
  "lessons": [
    {
      "id": "example-song-01-melody",
      "title": "Example Song - First Phrase",
      "description": "Play a short melody on the high E string.",
      "asset": "lessons/01-melody.json"
    }
  ]
}
```

Manifest cover and lesson paths are relative to that composition's directory.
Use local relative paths only, without URLs, absolute paths or `..` traversal.
Keep IDs unique and stable: saved progress and history depend on lesson IDs.
Renaming titles, replacing pictures or moving files must not reset those IDs.
Never reuse an existing ID for a different composition or exercise.

## Lesson JSON

Catalog version and score version are independent. Use score `schemaVersion: 1`
for ordinary melody lessons; use version 2 only when its expanded simultaneous
voice support is needed. This is a complete minimal score, not a complete curriculum:

```json
{
  "schemaVersion": 1,
  "title": "Example Song - First Phrase",
  "bpm": 60,
  "beatsPerMeasure": 4,
  "showChordNames": false,
  "lesson": {
    "instructions": "Play the thin high E string, then leave two beats of silence.",
    "selfPaced": false,
    "defaultSound": "beat",
    "previewMelody": true
  },
  "measures": [
    {"metronome": true, "notes": []},
    {"metronome": true, "notes": []},
    {
      "notes": [{"beat": 0, "duration": 2, "string": 0, "fret": 0}],
      "rests": [{"beat": 2, "duration": 2}]
    }
  ],
  "backing": {
    "measures": [{"notes": []}, {"notes": []}, {"notes": []}]
  }
}
```

- Always write two real empty count-in measures with `metronome: true`; music starts
  in measure 3 or later. The app does not add an invisible prefix.
- `beatsPerMeasure`: 2, 3 or 4, meaning 2/4, 3/4 or 4/4.
- `beat`: zero-based position within the measure. `duration`: quarter-note units,
  commonly 0.5 (eighth), 1 (quarter), 2 (half), 4 (whole). Events must fit the measure;
  a whole note cannot fit 2/4 or 3/4. Use supported written values from FORMAT.md.
- `string`: 0 = high e, 1 = B, 2 = G, 3 = D, 4 = A, 5 = low E. This is not human
  string numbering 1-6. `fret: 0` means open string; fret positions are integers.
- `rests` explicitly describes silence. Notes/rests must not overlap except for
  supported simultaneous note groups. Follow FORMAT.md for `tied` notation.
- `lesson.instructions` is nonblank. `defaultSound` is `beat`, `none` or `backing`.
  `previewMelody: true` demonstrates the written learner notes in the catalog preview;
  it does not add the learner's lead to backing during scored practice.
- `selfPaced: true` is for untimed practice with one to six distinct string/fret
  targets. It still needs valid score timing and both count-in measures.
- `chord` on a measure supplies harmony. Show chord names only when the student
  actually prepares that grip or arpeggio. Melody-only lessons normally set
  `showChordNames: false` and omit `chordFingerings`. If present, `chordFingerings`
  must describe the actual written partial/full grip, not an unrelated generic shape.
- Score v1 allows at most two synchronous untied voices on different strings, equal
  durations, MIDI 40-88, at least nine semitones apart, excluding near-exact integer
  harmonic pairs. Score v2 allows up to four such voices with at least two semitones
  between adjacent pitches and permits octaves. Neither allows staggered overlaps,
  unequal simultaneous durations or duplicate strings. Do not bypass validation.

### Backing and lyrics

Missing `backing` enables automatic guitar/piano synthesis. Explicit `backing` uses
only its authored guitar notes; empty backing measures mean silence. Its measure
count must match the student score, including two empty intro measures. Backing
notes use `beat`, `duration`, `string`, `fret` and optional `volume`; track/note gains
are in 0..1. Notes on the same backing string must not overlap. These notes never
enter student TAB or scoring. See FORMAT.md for a full audible example.

Optional `lyrics` contains `language` and ordered `lines`. Each line has a 1-based
`measure` including count-in, local `beat`, `duration`, and `words`. Each word has
`text`, `beat` relative to its line, and `duration`. Words may span several notes;
lines may span measures. Write repeated verses with their actual times. Respect
pickups, held words and rests, not a mechanical one-word-per-note mapping. Do not
attach sung lyrics to unrelated preparation exercises or instrumental compositions.
Lyrics must fit the song and be legally distributable. Read FORMAT.md and LYRICS.md.

## Required artwork workflow

For every new composition, add an appropriate image, normally `cover.webp`, **in
that composition's directory**, and set `"cover": "cover.webp"` in its `song.json`.
One image serves all lessons. Merely uploading an unreferenced file is not enough.

Use original, supplied, generated or appropriately licensed artwork. Prefer a
landscape WebP around 960 pixels wide, with a clear subject and no tiny text. PNG
and JPEG are also supported. Files must be at most 2 MiB and source dimensions at
most 4096 pixels per side; the app bounds decoded images to 1024 pixels.

If suitable artwork is not available yet, explicitly use the shared generic fallback:
omit `cover` and retain catalog `defaultCover`. Document that this is temporary.
Do not invent a nonexistent image path. Later add the real image and its `cover`
reference, or replace an existing cover file while preserving composition/lesson IDs.
Missing or invalid artwork falls back to the library default, then bundled app art.

Publishing the image and manifest on the library's main branch makes them available
to the compatible app's next automatic library refresh. Images participate in the
revision digest, so image-only changes propagate too, without rebuilding the APK.
Offline phones keep their current library until a successful refresh. This does not
change Welcome artwork, which is an app resource.

## AI artwork direction: put the learner first

The product goal is to help a beginner play songs they love, one achievable step at
a time. Carry the companion app's `docs/customer-experience-and-communication.md`
principles into this standalone library: warm, welcoming, encouraging and respectful
of children and adults. Artwork should invite “I would like to play this song”. It
must not imply guaranteed mastery, competition or an achievement not yet earned.

- Use an inviting hand-painted gouache/watercolor illustration with subtle paper
  texture, soft natural light, cream, honey/wood brown, peach and muted sage colors.
  Match the existing covers as a family without making every composition identical.
- Pick one recognizable subject or simple scene connected to the song's title,
  story or mood. Quiet Morning uses an acoustic guitar by a sunny cottage window;
  Amazing Grace uses a peaceful tree and path toward sunrise to suggest hope.
  A guitar need not appear on every cover. Treat cultural and religious origins
  respectfully; do not invent claims about a song's historical setting.
- Friendly does not mean infantile. Avoid intimidating concert virtuosity, pressure,
  trophies, scores, exaggerated celebrations, dark drama and cluttered imagery.
- Use a landscape 3:2 full-bleed composition. Keep key subjects away from edges and
  readable in both a wide card and a small central square crop. Prefer a strong
  silhouette and a quiet background over many tiny details.
- No baked-in titles, letters, logos, watermarks, borders, UI, TAB or fake music
  notation. The app supplies readable titles, actions and genuine progress separately.
- If people or instruments appear, inspect anatomy, hands, posture and guitar
  construction. Do not use decorative artwork as a technical fingering instruction.
- Generate a distinct asset per missing composition using the available image tool.
  Inspect existing artwork first. Preserve existing covers unless replacement is
  requested. Use original concepts, not an imitation of a named artist or copied cover.
- Inspect the generated result and exported WebP at full size and thumbnail size.
  Check subject, mood, crop safety, unwanted text and artifacts. Export to the
  composition directory, connect `cover` in the manifest, and verify it decodes.
  Keep a short record of tool and prompts with the artwork; raw large outputs do
  not belong in the app's downloadable assets.

Reusable AI prompt (replace the bracketed scene for each song):

```text
Use case: illustration-story.
Asset: one landscape 3:2 song cover for Plucksy, a welcoming guitar-learning app
for children and adults. Song: [title]. Scene: [one clear subject and setting
connected to the song]. Warm hand-painted gouache and watercolor, subtle paper
texture, cream, honey amber, muted sage and peach palette, soft natural light.
Mood: approachable, hopeful, calm enjoyment of learning music, never intimidating.
Composition: one clear subject, readable at thumbnail size, important details
inside safe margins, suitable for wide and central square crops, quiet background.
Full bleed, opaque. No text, lettering, logo, watermark, border, UI, scores,
trophies or music notation. Plausible instrument construction and anatomy if shown.
```

## Validation and publication

- Parse all JSON and check every catalog/manifest/lesson/cover reference, unique ID,
  order, count-in, measure boundary, rest, chord grip and backing alignment.
- Audition the melody alone, preview and backing. Compare adjacent lessons for sudden
  difficulty jumps; verify fingering on a guitar. Synthetic audio is not proof that
  an arrangement is comfortable or reliably recognized acoustically.
- In the companion Android checkout with this library revision, run JDK 17 checks:
  `./gradlew testDebugUnitTest lintDebug assembleDebug`. Inspect TAB, practice excerpts,
  PDF and composition artwork. Preserve existing musical regression tests; update
  catalog expectations deliberately when adding approved content.
- Stay within archive limits: JSON 1 MiB/file, image 2 MiB/file, ZIP download 20 MiB,
  expanded archive 64 MiB. The app validates all required scores before switching
  revisions; invalid content leaves the previous offline library active.
- New unsupported JSON features require a compatible app release, not just a data push.
- When publication is requested, commit/push the library first, then update and commit
  the parent app's submodule pointer for the bundled offline version. Do not claim
  changes reached phones before publication. Keep work local until publication is requested.
- Keep this guide concise and current. Put song-specific sources, lesson maps and
  decisions in dedicated Markdown documents rather than growing the global checklist.
