# Lyrics coverage audit

Audited all35 lesson JSONs, 2026-11-12. Optional timed lyrics now cover20 lessons across three compositions,198 line occurrences including explicit training repetitions. Notes, chords, backing, instructions, tempos, IDs and catalog order are unchanged.

| Composition | Coverage | Decision |
| --- | --- | --- |
| Hot Cross Buns | Lessons03-08,48 lines | Match actual melody phrases; rhythm preparation and untimed targets01-02 remain without lyrics. |
| Mary Had a Little Lamb | All five lessons,50 lines | Two opening-phrase preparations plus two complete verses. |
| Twinkle, Twinkle, Little Star | Lessons02-10,100 lines | Actual whole phrases or sung fragments; untimed note targets01 remain without lyrics. |
| Quiet Morning | None | Original instrumental picking study, no established sung words. |
| Amazing Grace | Pending | Existing score is guitar accompaniment, not a written vocal melody. Word-level cues and vocal pickup still need an explicit verified vocal timing map. Do not invent them from chord changes. |

## Mary

Text basis: Sarah Josepha Hale's1830 poem [Mary's Lamb, University of Toronto Libraries](https://rpo.library.utoronto.ca/content/marys-lamb). The familiar sung repetition follows the actual existing melody. The extra final B attack in the sixth bar carries the word Its, so the final text line begins at beat3 of that bar, not at the next barline. The last word holds across the complete final G whole note. The first two opening-phrase preparations repeat only their matching text; preparation rests have no highlighted word.

## Twinkle

Text basis: Jane Taylor's1806 [The Star, Academy of American Poets](https://poets.org/poem/star/print), identified there as public domain. Use its first four lines, with opening/second-line reprises matching the existing12-bar A-B-C-C-A-B tune. The two identical C melodies carry distinct consecutive lines, rather than assigning the same words solely from pitches. Short D-bass/fill preparations show only the corresponding ending or opening fragment. A word may span several melody attacks and offbeat guitar fills never create extra sung words.

## Remaining compositions

Quiet Morning is intentionally instrumental; adding an original vocal text would be a new creative decision.

Amazing Grace has a known historical text ([Olney Hymns background, Cowper & Newton Museum](https://cowperandnewtonmuseum.org.uk/amazing-grace-/)), and the approved teacher [accompaniment sheet](https://relaxandlearnguitar.com/wp-content/uploads/2024/04/Amazing-Grace-Fingerstyle-tab.pdf) aligns lines with four-chord groups. It does not supply syllable-level vocal note durations. The current JSON writes only the picking accompaniment, including preparation and rest bars. A future pass should choose the vocal pickup placement explicitly, confirm all four phrases against these16 accompaniment bars, and only then encode exact word timing. Current lyric validation deliberately excludes the two count-in bars. No arbitrary syllable timings or modern adapted verses are added here.

## Checks

The parent app's CatalogLyricsTest checks coverage, all word onsets against actual melody attacks, Mary's inside-bar pickup and whole-note ending, both Twinkle bridge lines and exclusion of offbeat fills. Existing curriculum tests preserve pitches/rhythm/voicings. A JSON comparison against the prior library revision verifies that only the optional lyrics field changed in the14 added Mary/Twinkle lesson files. Validate the real published GitHub ZIP with the app installer before pinning its revision.
