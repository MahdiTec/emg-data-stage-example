# Quality report (example)

Rule, written before any score: reject a trial if a sample sits at the limit of the converter (0 or 1023), or if more than 1 % of its samples are missing.

| File | Session | Trials | Rejected | Reason |
|---|---|---|---|---|
| P01_S01_R01.csv | S01 | 5 | 0 | kept |
| P01_S01_R02.csv | S01 | 5 | 2 | 2 trials: samples at the limit of the converter |
| P01_S01_R03.csv | S01 | 5 | 0 | kept |
| P01_S01_R04.csv | S01 | 5 | 0 | kept |
| P01_S02_R01.csv | S02 | 5 | 0 | kept |
| P01_S02_R02.csv | S02 | 5 | 0 | kept |
| P01_S02_R03.csv | S02 | 5 | 0 | kept |
| P01_S02_R04.csv | S02 | 5 | 0 | kept |
| P01_S03_R01.csv | S03 | 5 | 1 | 1 trial: 3 % of the samples missing |
| P01_S03_R02.csv | S03 | 5 | 0 | kept |
| P01_S03_R03.csv | S03 | 5 | 0 | kept |
| P01_S03_R04.csv | S03 | 5 | 0 | kept |
| P01_S04_R01.csv | S04 | 5 | 0 | kept |
| P01_S04_R02.csv | S04 | 5 | 0 | kept |
| P01_S04_R03.csv | S04 | 5 | 0 | kept |
| P01_S04_R04.csv | S04 | 5 | 2 | 2 trials: samples at the limit of the converter |
| P01_S05_R01.csv | S05 | 5 | 0 | kept |
| P01_S05_R02.csv | S05 | 5 | 0 | kept |
| P01_S05_R03.csv | S05 | 5 | 1 | 1 trial: 2 % of the samples missing |
| P01_S05_R04.csv | S05 | 5 | 0 | kept |
| P01_S06_R01.csv | S06 | 5 | 1 | 1 trial: samples at the limit of the converter |
| P01_S06_R02.csv | S06 | 5 | 0 | kept |
| P01_S06_R03.csv | S06 | 5 | 0 | kept |
| P01_S06_R04.csv | S06 | 5 | 0 | kept |

**Totals.** 120 trials recorded. 7 rejected: 5 for samples at the limit of the converter (an artifact), 2 for missing samples (a gap). 113 kept: 75 for training, 38 for the test.

**Noise.** Write here the size of your signal at rest, and compare it with the size during movement.

**Outliers.** Write here any recording that is far from the others of its class, and whether it is an error or a real rare case.
