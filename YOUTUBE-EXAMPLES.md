# YouTube examples for the remaining courses

Prepared and approved for publication 2026-11-20. Existing
Hot Cross Buns and Before You Play assignments remain unchanged. Video links
do not grant redistribution rights to recordings, TAB or modern arrangements.
No audio, TAB or video was downloaded or copied into these changes.

## Assigned clips

All times are absolute source-video seconds. Composition and exercise metadata
are independent. The table distinguishes a complete example from a technique
reference; a technique clip is not an exact performance of our exercise.

| Course / placement | Creator and source | Interval | Fit and limits |
| --- | --- | --- | --- |
| Amazing Grace composition and lesson 4 | [Relax and Learn Guitar](https://www.youtube.com/watch?v=6AMGNWBoHcc&t=408s) | 6:48-7:14, 408-434 | Sung G/C/D accompaniment, not solo chord-melody. Follow our TAB for the exact tempo, partial shapes, pickup and repetitions. |
| Amazing Grace lesson 1 | Same source | 2:50-4:43, 170-283 | Finger allocation and bass-3-2-3-1-2 pattern, matching our six eighth notes in 3/4. Includes explanation of moving the thumb for later chords. Anchoring the little finger is presented as optional by the teacher, not a requirement. |
| Amazing Grace lesson 2 | Same source | 4:59-5:27, 299-327 | G to C and back, before the D explanation. Our preparation rests and repeated practice are app-specific. |
| Amazing Grace lesson 3 | Same source | 5:27-6:02, 327-362 | D bass and return to G, then the remaining progression. Not an exact isolated rendition of our practice sequence. |
| Mary composition | [Hub Guitar](https://www.youtube.com/watch?v=HHJN1uiY0GA&t=147s) | 2:27-2:46, 147-166 | Instrumental example from the author's Instrumental chapter. Same G/Em/D direction as our final course. |
| Mary lesson 5 | Same source | 0:34-2:01, 34-121 | Explains the G, Em and D voices and melody. D includes A-string fret 5 and D-string fret 4, rather than silently substituting a different open-D voicing. Earlier steps deliberately omit some voices. |
| Twinkle composition | [Six String Fingerpicking](https://www.youtube.com/watch?v=caA6Pr1scgg&t=8s) | 0:08-0:46, 8-46 | Complete G-major fingerstyle example. Contains the optional D/F# variation taught in lesson 10, so it is a target/inspiration, not a note-for-note model for beginner steps or our simpler D version in lesson 9. Attribution explicitly labels the D/F# version. |
| Twinkle lesson 10 | Same source | 3:46-4:25, 226-265 | D/F# bass on low E fret 2, G-string fret 2, with open D-string filler. The teacher offers a finger alternative to using the thumb on the neck. |
| Quiet Morning lesson 1 | [Bradford Werner](https://www.youtube.com/watch?v=RDOqubQd9Jo&t=656s) | 10:56-14:06, 656-846 | General finger movement. Technique support, not our exact i-m-a-m-i pattern or original composition. |
| Quiet Morning lesson 2 | Same source | 14:06-16:55, 846-1015 | General thumb position/movement. Does not demonstrate our exact bass-plus-G onset. |

## Evidence and timing confidence

- Chrome YouTube pages checked 2026-11-20 for Mary, Twinkle and Amazing Grace:
  title, creator, duration, chapter descriptions and timestamped transcript.
  Durations were 3:54, 9:11 and 8:09 respectively. Clip boundaries use these
  descriptions and transcript music/speech transitions, not a frame-accurate edit.
- Amazing Grace's source chapters are Chords 0:37, Fingerstyle picking pattern
  2:37 and Play through 4:53. Despite the latter label, the actual sung example
  begins around 6:48. Do not label 4:53 as a performance-only clip.
- Mary source chapters: Singalong 2:01, Instrumental 2:27, Conclusion 2:59.
  The instrumental music ends around 2:46, before the chapter ends.
- Twinkle transcript identifies G/C, low E fret 3, and D/F# at 3:46-4:25.
  [Creator's lesson page](https://sixstringfingerpicking.com/songs/twinkle-twinkle-little-star-guitar-lesson/)
  confirms standard tuning, no capo and G major.
- Werner intervals are the creator's published chapter boundaries on the
  [official technique page](https://www.thisisclassicalguitar.com/right-hand-technique-for-classical-guitar/).
  The chapter link resolves to video RDOqubQd9Jo, already used in Level 0.
- This pass verified metadata/transcripts and existing score/source documents,
  not a complete visual audition, region-by-region embed availability, or an
  in-app device playback pass. YouTube availability and timing can change.

## Deliberately unassigned / next proposals

- **Quiet Morning composition and steps 3-8:** our original study has no exact
  external performance. Prefer one short original recording of C-C-G-G-D-D-G-G
  at 40 BPM in 3/4, with close-ups of our partial C/G shapes and standard D.
  Do not use an unrelated video entitled Quiet Morning as the whole-song demo.
- **Mary steps 1-4:** the final video immediately starts with several simultaneous
  voices. Keep it out of these earlier steps until exact melody-only and staged
  bass examples have been auditioned, or record our own four progressive clips.
- **Twinkle steps 1-9:** the source lesson introduces filled fingerstyle and D/F#.
  Keep early-step icons absent rather than imply those skills are required.
  For step 9, an original simple-D demonstration would match better than the
  source's F# bass. The composition clip remains an optional later goal.

The learner's notes, accompaniment, lyrics, IDs and progress keys are unchanged.
Publish the library only when requested, then update the parent app gitlink.

## Validation

JDK 17 focused Gradle run passed all 26 tests in SongLessonVideoTest,
SongCatalogTest, AmazingGraceTest, QuietMorningTest and SongChordPolyphonyTest.
Parsed all 11 modified JSONs and compared each to HEAD after removing only its
new youtubeVideo field: all pre-existing data is identical. git diff --check
passed. No application code or existing Hot Cross Buns assignments changed.
