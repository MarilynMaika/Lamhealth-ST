19 Nov 2026 · split v1 · Test = C003 (Diarrhoea), C004 (Chest pain), drawn at random with seed 2026 before any training. 162 test pairs scored; 20 excluded because the same Lamnso sentence occurs in training. Train = 581 pairs from 9 consultations.
# Cleaning log

Every decision about the data: what was found, what was done, and why.
Raw files in `data/raw/` are never edited; all changes are made in notebook 01 and recorded here.
Newest entries at the bottom.

## Data v1 (19 Nov 2026)

| Date | Version | Item | What was found | Decision and reason |
|---|---|---|---|---|
| 19 Nov 2026 | v1 | C005 Hypertension | Translation had unresolved issues | Excluded from the parallel data; status `excluded` in inventory.csv |
| 19 Nov 2026 | v1 | C011, C012, C015, C024, C025 | Not localised | Recorded as not prepared; 20 of 25 consultations localised |
| 19 Nov 2026 | v1 | C007 English | Two files with identical SHA-256 | Kept C007_T2DM__1.csv; the other is a duplicate |
| 19 Nov 2026 | v1 | C023 English | Two files; same text, one with a stray '-' in an extra column (row T098) | Kept C023 PCOS.csv |
| 19 Nov 2026 | v1 | C008, C014 | Column headers mislabelled: Lamnso stored under "English Utterance" | Corrected with a column map in notebook 01; verified by checking for Lamnso characters |
| 19 Nov 2026 | v1 | C001 | Turn column named "ID" instead of "Turn" | Mapped to turn in the column map |
| 19 Nov 2026 | v1 | Speaker labels | 11 spellings of 2 speakers (case, Ŋ/N, trailing spaces, a typo, English labels) | Added a `role` column (Doctor/Patient); original speaker text kept |
| 19 Nov 2026 | v1 | C001 T077, C006 T077, C006 T080 | No speaker label | Set to Doctor after reading the English text |
| 19 Nov 2026 | v1 | C003 T058 English | Garbled dash "â€”" from an earlier wrong-encoding save | Replaced with "—"; the only garbled text found in 764 rows |
| 19 Nov 2026 | v1 | All text | Tone marks stored in decomposed form in 749 Lamnso cells; spaces at cell edges (244 Lamnso, 5 English, 10 speaker) | Unicode NFC normalisation and edge-space trimming; wording and punctuation unchanged |
| 19 Nov 2026 | v1 | C006 T029; C010 last 4 rows | No turn number | Kept: they are real turns. Pair IDs use position in the file, so no turn numbers were invented |
| 19 Nov 2026 | v1 | C001_077 | No Lamnso translation | Dropped; listed in dropped_v1.csv |
| 19 Nov 2026 | v1 | Data v1 | 763 pairs from 11 consultations | Frozen as parallel_v1.csv; SHA-256 in manifest_v1.csv |
| 19 Nov 2026 | v1 | Test split | — | C003 (Diarrhoea) and C004 (Chest pain) held out, drawn at random with seed 2026 before any training. 162 test pairs scored, 20 excluded as repeats of training sentences, 581 train |

## Data v2: alignment fixes (19 Nov 2026)

Found in exploration (notebook 02): pairs whose Lamnso and English lengths differed sharply. Each was read and decided by the researcher, who reads Lamnso. Details in fixes_v2.csv.

| Date | Version | Pair | What was found | Decision and reason |
|---|---|---|---|---|
| 19 Nov 2026 | v2 | C001_076 | Lamnso far longer than the English; appears to include the untranslated C001_077 | Excluded |
| 19 Nov 2026 | v2 | C003_097 (test) | Lamnso translates only the final question | English shortened to "Do you understand?" |
| 19 Nov 2026 | v2 | C004_043 (test) | Lamnso has extra sentences beyond "No headaches." | Trimmed to the first sentence |
| 19 Nov 2026 | v2 | C006_070 | Cell also contained a copy of C006_072's translation | Trimmed to the first sentence, which matches the English |
| 19 Nov 2026 | v2 | C006_072 | Cell held its own translation plus most of C006_073's | Kept its own part; moved the rest to C006_073 |
| 19 Nov 2026 | v2 | C006_073 | Lamnso incomplete (last sentence only) | Completed with the text moved from C006_072 |
| 19 Nov 2026 | v2 | C007_023 | English said more than the Lamnso | English rewritten by the researcher: "There hasn't been any change." |
| 19 Nov 2026 | v2 | C013_056 | English said more than the Lamnso | English rewritten by the researcher: "Thank you, Doctor." |
| 19 Nov 2026 | v2 | 8 other flagged pairs | Length ratio above 2.5 (numbers, short answers, greetings) | Checked; no change, as the difference is natural |
| 19 Nov 2026 | v2 | Test split | Same test consultations as v1 (C003, C004) | Counts in split_v2.csv |