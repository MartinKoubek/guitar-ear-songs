# Song JSON format, schemaVersion1

The current JSON files are complete examples. Preserve the format supported by the Android parser.

## Catalog

`assets/songs/catalog.json` contains `schemaVersion`, `levelCount`, ordered `songs`, optional `levels` and optional `sublevels`. Each song has a stable lowercase-hyphenated `id`, `level`, English `title`/`description`, relative `asset` such as `songs/level-1-hot-cross-buns-08-across-strings.json`, optional `section` and optional `sublevelId`. Referenced groups must exist in the same level and contain songs. IDs are used for saved progress and must not be renamed during editorial changes.

## Learner part

Root fields: `schemaVersion:1`, `title`, positive `bpm`, `beatsPerMeasure` (2,3,4), optional `showChordNames` and ordered `measures`. First two measures explicitly contain `metronome:true, notes:[]` with no chords/rests. Later measures contain `notes` and optional `rests`/`chord`; no hidden count-in is inserted.

Each note has local measure `beat`, `duration` (0.5,1,2,4 quarter-note beats), integer `string` (0=high e,1=B,2=G,3=D,4=A,5=low E), `fret` (0-24), optional `tied` (only duration2 in the current tie notation). Events must fit within the measure. A rest has `beat`/`duration`. Notes/rests must be ordered and cannot overlap except supported synchronous dyads.

Dyads contain at most two untied notes on distinct strings with identical onset/duration. Pitches must be MIDI40-88 and at least9semitones apart; near-exact integer harmonic pairs (multiples2-16 within8cents, including octaves) are unsupported. Staggered overlap, unison and unequal dyad durations are rejected.

## Guided lessons

Optional root `lesson`: nonblank English `instructions`, boolean `selfPaced` (defaultfalse), `defaultSound` (`beat`, `none`, `backing`; defaultbeat), boolean `previewMelody` (defaultfalse). Untimed lessons require one to six distinct string/fret targets. They retain valid JSON timing/count-in for compatibility but use manual target selection and Finish rather than a playback clock. `previewMelody` demonstrates learner notes only in the separate preview copy.

## Independent guitar backing

Optional `backing` contains `volume` (0-1) and `measures` aligned with the full learner measure count, including two empty intro bars. Backing note fields: local `beat`, positive `duration`, integer `string`/`fret` and optional `volume` (0-1). Events fit their measure; the same backing string cannot overlap itself, while different strings may play together. Missing backing uses automatic harmony; an explicitly empty backing is silent. Backing notes are never learner scoring targets.

## Validation

The Android project contains authoritative Kotlin validation and regression tests. Run its JDK17 `./gradlew testDebugUnitTest lintDebug assembleDebug` with this library checked out as its submodule. Do not publish malformed catalogs or songs, and preserve working revisions for older app versions.


## Version 2 guitar chords

Mary Level2 scores use `schemaVersion:2` and require an updated app. The catalog remains schemaVersion1. Version2 supports synchronous untied groups of 2-4 distinct strings/pitches in MIDI40-88, equal duration, adjacent sorted pitches at least two semitones apart, including octaves. Reject unisons, more than four voices, unequal durations and staggered overlaps. Version1 keeps its separated-dyad restrictions.

Optional `chordFingerings` is a map of chord name to nonblank English actual partial-shape instructions. It does not change the note data. Mary uses original D (A5/D4/G2) to retain the A3 melody. All five Mary lessons include real count-in, opening-phrase preparation and two full eight-bar repetitions. Authored backing is explicitly silent; `previewMelody:true` demonstrates the learner's written part.

Expanded chord listening uses 8192-sample windows, a 32768-point padded FFT and a 4096-sample hop (about 93ms), skipping redundant monophonic analysis. V1 keeps its original 2048-sample hop. V2 polyphonic practice is capped at 90BPM for quarter notes / 50BPM with eighths, while preserving authored defaults. Three stable frames plus the 200ms analysis-tail guard still fit the written note windows.

Twinkle uses schema2 unchanged. The final picking texture explicitly writes melody plucks as eighth notes on integer beats and lighter open-string fills on half beats; original half-note phrase endings are preserved. All groups have equal duration and no staggered overlap. The D/F# bonus changes D downbeat bass to F#2 while retaining open-D fills. Stable group: twinkle-twinkle-little-star, Level2, ten lessons. Main backing is silent and previews demonstrate written notes.

## Optional timed lyrics (score schema1 and2)

A lyric-capable APK accepts root `lyrics: {"language":"en","lines":[...]}`. `language` is optional; missing/null lyrics hides all lyric UI. Each line has 1-based `measure` including the two empty intro bars, local `beat`, positive `duration` in quarter-note beats, and ordered `words`. Each word has nonblank `text`, a `beat` relative to its line start, and positive `duration`. Example:

```json
"lyrics": {
  "language": "en",
  "lines": [{
    "measure": 3, "beat": 0, "duration": 4,
    "words": [
      {"text":"Hot", "beat":0, "duration":1},
      {"text":"cross", "beat":1, "duration":1},
      {"text":"buns!", "beat":2, "duration":2}
    ]
  }]
}
```

Lyrics start no earlier than measure3. Lines may span bars but must fit the song; words must fit their line. All times are finite JSON numbers, ordered without overlaps; gaps are allowed. Include punctuation in words. One token may cover several notes; repeat lines explicitly at the actual repeated times. Tokens join with one space. Limits: 512 lines, 64 words/line,128 characters/token,512 characters/line,64,000 text characters total; no blank/control-character tokens. Older APKs ignore this optional field. Do not change notes/backing/IDs to add lyrics. Only use text that may be distributed with the library. The current timed full player displays/highlights it; static practice, untimed targets, synthesized audio and PDF do not render/sing it.
