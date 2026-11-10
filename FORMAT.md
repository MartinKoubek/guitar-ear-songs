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
