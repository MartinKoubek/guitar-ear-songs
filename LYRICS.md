# Lyrics coverage audit

Audited all 35 lesson JSONs, 2026-11-12. Optional timed lyrics cover 21 lessons across four compositions, 206 line occurrences including explicit training repetitions. Amazing Grace lesson04 adds one explicit guitar-rest pickup bar after the two count-in bars; its 192 guitar notes, chord sequence, tempo, ID and order are unchanged. Other scores are unchanged.

| Composition | Coverage | Decision |
| --- | --- | --- |
| Hot Cross Buns | Lessons03-08,48 lines | Match actual melody phrases; rhythm preparation and untimed targets01-02 remain without lyrics. |
| Mary Had a Little Lamb | All five lessons,50 lines | Two opening-phrase preparations plus two complete verses. |
| Twinkle, Twinkle, Little Star | Lessons02-10,100 lines | Actual whole phrases or sung fragments; untimed note targets01 remain without lyrics. |
| Quiet Morning | None | Original instrumental picking study, no established sung words. |
| Amazing Grace | Lesson04, 8 lines | First verse twice, mapped independently to the sixteen-bar New Britain vocal tune. One extra pickup bar before the first round; the existing rest bar supplies the second pickup. |

## Mary

Text basis: Sarah Josepha Hale's1830 poem [Mary's Lamb, University of Toronto Libraries](https://rpo.library.utoronto.ca/content/marys-lamb). The familiar sung repetition follows the actual existing melody. The extra final B attack in the sixth bar carries the word Its, so the final text line begins at beat3 of that bar, not at the next barline. The last word holds across the complete final G whole note. The first two opening-phrase preparations repeat only their matching text; preparation rests have no highlighted word.

## Twinkle

Text basis: Jane Taylor's1806 [The Star, Academy of American Poets](https://poets.org/poem/star/print), identified there as public domain. Use its first four lines, with opening/second-line reprises matching the existing12-bar A-B-C-C-A-B tune. The two identical C melodies carry distinct consecutive lines, rather than assigning the same words solely from pitches. Short D-bass/fill preparations show only the corresponding ending or opening fragment. A word may span several melody attacks and offbeat guitar fills never create extra sung words.

## Remaining compositions

Quiet Morning is intentionally instrumental; adding an original vocal text would be a new creative decision.

## Amazing Grace

Vocal reference: [Indiana University teaching score, Open Hymnal Project](https://cpb-us-w2.wpmucdn.com/blogs.iu.edu/dist/c/488/files/2020/08/Melody-Options-Non-Voice-Majors.pdf), page 1, New Britain in 3/4, John Newton first verse and public-domain Excell setting. The page was rendered and visually checked. The separate [Timeless Truths score](https://library.timelesstruths.org/library/music/A/Amazing_Grace/Amazing_Grace.pdf) confirms the syllable assignments but shortens the sustained endings; use the university's sixteen-bar version to match our sixteen-bar accompaniment. No graphical score or recording is redistributed.

Only the complete accompaniment lesson gets lyrics. Lessons01-03 are guitar-pattern/chord preparations, not complete sung verses. Keep both original count-in bars empty. Add a third, fully notated guitar-rest bar, starting Amazing on its third beat. The first guitar downbeat follows on measure4. The existing between-round rest bar is now measure20; its third beat carries the second Amazing. No hidden/negative phase, no singing during count-in and no change to the original sixteen-bar guitar parts.

Each four-line verse begins one quarter-note before the first accompaniment downbeat and spans 48 beats. Amazing is one word across the pickup plus maz/ing (4 beats); me and see each hold for 5 beats, following the ties. Once, was, now and am each keep their word highlighted across their slurred notes. These are vocal cues, not the six guitar plucks in each measure. Both rounds repeat the same first verse.

| Line | Source measure / local beat, rounds 1 and 2 | Word offsets and lengths in quarter-note beats |
| --- | --- | --- |
| Amazing grace, how sweet the sound, | 3/2 and 20/2 | Amazing 0:4, grace 4:2, how 6:1, sweet 7:2, the 9:1, sound 10:2 |
| That saved a wretch like me! | 7/2 and 24/2 | That 0:1, saved 1:2, a 3:1, wretch 4:2, like 6:1, me 7:5 |
| I once was lost, but now am found, | 11/2 and 28/2 | I 0:1, once 1:2, was 3:1, lost 4:2, but 6:1, now 7:2, am 9:1, found 10:2 |
| Was blind, but now I see. | 15/2 and 32/2 | Was 0:1, blind 1:2, but 3:1, now 4:2, I 6:1, see 7:5 |

Local beat2 means the third beat, using the JSON's zero-based offsets. Last see releases one beat before the final guitar bar ends. The remaining beat and the following guitar-rest bar are unhighlighted until the second pickup. The final rest bar has no words. Learn guitar first; adding a live singer may affect the guitar microphone judge. Physical guitar-and-voice verification remains outstanding.

## Checks

The parent app's CatalogLyricsTest checks coverage, melodic-lesson word onsets against actual melody attacks, Mary's inside-bar pickup and whole-note ending, both Twinkle bridge lines and exclusion of offbeat fills. Existing curriculum tests preserve pitches/rhythm/voicings. AmazingGraceTest checks the independent vocal map, pickup bars, tied endings, neutral breaths, repeat offset and practice clipping. Amazing Grace is explicitly excluded from the melody-attack invariant because its TAB is accompaniment. A structural comparison verifies its original 192 guitar notes and chord sequence are unchanged apart from the explicit pickup-bar offset. Validate the real published GitHub ZIP with the app installer before pinning its revision.
