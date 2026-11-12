# Quiet Morning - Level 1 picking study

Original study based on the user's approved pattern, not an arrangement of a named folk melody. Place after Hot Cross Buns. Eight cumulative lessons, all at 40 BPM in 3/4, with two explicit count-in measures. The same i-m-a-m-i pattern remains throughout: G for one quarter, then B/e/B/G as four eighths. From step 2 the thumb plucks the written bass together with the initial G string.

| Step | Skill | Repetition |
| --- | --- | --- |
| 1 | Open treble strings, i-m-a-m-i | Four attempts with one rest bar each |
| 2 | Add open low E with the first G | Four attempts with rest bars |
| 3 | Partial C: A3 and B1, open G/e | Four attempts with rest bars |
| 4 | Partial G: low E3 and high e3, open G/B | Four attempts with rest bars |
| 5 | C-C-G-G | Twice, rest after each phrase |
| 6 | Standard open D: D0/G2/B3/e2 | Four attempts with rest bars |
| 7 | G-G-D-D-G-G | Twice, rest after each phrase |
| 8 | C-C-G-G-D-D-G-G | Twice, one rest bar between rounds and at the end |

Only frets 0-3, no barre, no 2-4-5 stretch. The C/G partial shapes deliberately omit unused strings and require two fingers; D uses three. Chord names/fingering instructions appear only from step 3, where the learner actually holds and arpeggiates that grip. The early open-string exercises have no labels. Right-hand names are authored instructions; no new finger-marker renderer is claimed.

Score schema2 supports the close bass/treble pair and G octave. Notated durations are articulated, non-overlapping attacks supported by the current parser. Natural string ringing is allowed; microphone testing on a real guitar remains necessary, especially the G octave. Preview demonstrates the student's written part; main Backing is explicitly silent to avoid playing the expected bass for the learner. Beat remains selectable. There is no new song-specific artwork: omission of cover uses the library's universal illustration.

## Next familiar song candidate

Recommend a simple **Amazing Grace accompaniment in G** with G/C/D and the same 3/4 picking cycle. This is accompaniment for singing/humming, not a claim that the fixed picking pattern alone reproduces the tune. Do not silently substitute a more difficult chord-melody arrangement.

Sources checked 2026-11-12:
- https://relaxandlearnguitar.com/wp-content/uploads/2024/04/Amazing-Grace-Fingerstyle-tab.pdf: teacher's G/C/D, 3/4 accompaniment example, with a different picking pattern. Reference only; no copied arrangement or lyrics added.
- https://www.andyguitar.co.uk/videos/lesson-3-easy-fingerstyle-for-beginners: beginner melody-only Amazing Grace, explicitly distinguishes later chord-melody work and confirms 3/4.

Only Quiet Morning is implemented in this change. Amazing Grace remains a recommendation for the next step. Existing Mary and all previous scores remain unchanged.

## Validation

QuietMorningTest verifies every event's right-hand order, timing, bass position, easy frets, chord visibility, explicit rests, preview separation and complete repeated progression. Existing catalog, Home, archive, PDF and music tests are updated for 31 lessons and four compositions. Song-library retains the existing default artwork fallback.
