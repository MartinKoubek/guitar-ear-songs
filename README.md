# Guitar Ear Songs

Public JSON content library for the Guitar Ear Android app. The current reference curriculum is **Hot Cross Buns**, taught in eight progressive Level1 lessons. Level2 adds five Mary Had a Little Lamb lessons from melody to four-note fingerstyle chords (song schemaVersion2, updated app required).

| Step | Lesson | Default pace |
| --- | --- | --- |
| 1 | Right Hand & Rhythm | 60 BPM |
| 2 | First Fretted Notes | Untimed |
| 3 | First Musical Phrase | 60 BPM |
| 4 | The Quicker Middle | 60 BPM |
| 5 | The Complete Tune | 64 BPM |
| 6 | First Bass | 50 BPM |
| 7 | Alternating Bass | 50 BPM |
| 8 | Melody Across Strings | 45 BPM |

## Layout

- `assets/songs/catalog.json`: ordered levels, song groups and stable lesson IDs.
- `assets/songs/*.json`: learner tablature, rhythm, instructions and independent guitar backing.
- [REFERENCE.md](REFERENCE.md): approved teaching progression.
- [FORMAT.md](FORMAT.md): JSON format and validation boundaries.

The library is consumed as the `song-library` Git submodule of `MartinKoubek/guitar-ear`. Android packages the `assets` directory without changing the in-app `songs/...` paths. Each app commit pins a specific library commit.

Clone the complete app with its content:

```sh
git clone --recurse-submodules git@github.com:MartinKoubek/guitar-ear.git
```

For an existing app checkout:

```sh
git submodule update --init --recursive
```

## Editing content

Keep existing IDs stable. Update the song JSON and catalog together. Validate changes using the Android project's JDK17 unit/lint/build checks before publishing. Commit and push library changes first, then update the app's submodule pointer when that version should be bundled.

This repository provides public content files. Download/synchronisation behavior in the phone app is a separate feature; the submodule manages source checkouts and bundled content.

Level2 also includes ten Twinkle, Twinkle, Little Star lessons: six melody targets, phrases, full melody, E/A/D bass, offbeat picking, full G/C/D fingerstyle and an optional D/F# bass variant. This is an independent traditional-tune arrangement. The current catalog has23 lessons and uses the existing schema2 app reader; no new APK feature is needed for these JSONs.
