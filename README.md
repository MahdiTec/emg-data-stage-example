# Example: Report 1, the data stage

> **This is an example.** Every number here is invented, and the files in `data/raw/` are empty. It shows what your own repository should hold and how short your answers can be. Do not copy the values. Your own protocol will differ.

Course: M6 Machine Learning and IoT apps. Project: tell a hand movement from rest with one muscle signal.

## The team

| Member code | GitHub user | In charge of | AI tool |
|---|---|---|---|
| M01 | @example-user-1 | data and metadata | Claude Desktop |
| M02 | @example-user-2 | code and versions | Visual Studio Code with Claude |
| M03 | @example-user-3 | quality report | Claude in the browser |
| M04 | @example-user-4 | protocol and cue video | another tool, named here |

Every member has at least one commit. See the commit list of this repository. We measure one person, member M01. In the data that person has the code P01.

## The six parts

### 1. Data acquisition
24 recordings, 120 trials, 6 sessions, 1 person. One sensor on the forearm flexors of the right arm, sampled at 1000 Hz, measured from the time column. The person watches `cue/cue-video.mp4`. One trial lasts 10 s.

**Evidence:** `data/raw/` (24 files), `data/metadata.csv` (24 rows), `cue/`.

### 2. Task
The person closes the right hand into a fist and holds it. Two classes: movement and rest. The person sits, with the forearm on the table and the palm up.

**Evidence:** `PROTOCOL.md`, `figures/placement_S01.jpg`.

### 3. Trial and cue timing
| Window | Seconds | What the person sees |
|---|---|---|
| Rest before | 0 to 3 | REST |
| Warning cue | 3 to 4 | GET READY |
| Action window | 4 to 8 | MOVE |
| Rest between trials | 8 to 10 | REST |

One recording holds 5 trials, so it lasts 50 s.

**Evidence:** `cue/cue-video.mp4`, the columns `rest_s`, `warning_s`, `move_s`, `between_s` of `data/metadata.csv`, `figures/one_recording_marked.png`.

### 4. Sessions
1 person. 6 sessions on 3 different days. Every session starts with new electrodes, placed again from zero. Each session has 4 recordings.

**Evidence:** the columns `participant`, `session` and `date` of `data/metadata.csv`, one photo per session in `figures/`.

### 5. Cleaning
Filters: a band-pass filter and a notch filter at 60 Hz, the frequency of the power line in Mexico. The type and the limits of the band-pass are in `PROTOCOL.md`, with their source. The upper limit is below half of our sampling rate.
Rule to reject a trial, written before we looked at any score: reject it if a sample sits at the limit of the converter (0 or 1023), or if more than 1 % of its samples are missing.
Result: 7 of 120 trials rejected. 113 remain. The raw files are untouched.

**Evidence:** `QUALITY-REPORT.md`, `code/check_quality.py`, the columns `trials_rejected` and `notes` of `data/metadata.csv`.

### 6. Fair split
Training: sessions S01 to S04, 75 trials. Test: sessions S05 and S06, 38 trials, recorded on another day with new electrodes. The model never sees these two sessions in training. Limit: the model is built and tested on one person and one movement. We do not claim that it works for other people. We do not shuffle windows of one recording between training and test.

**Evidence:** the column `set` of `data/metadata.csv`.

## What comes next
Our decisions about features, the model and the route are in `DECISIONS.md`. The rationale of each member is in `rationale/`.

## Where to search
- How to organise the files: Wilson and others, [Good enough practices in scientific computing](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510), 2017.
- What to report about a muscle recording: Merletti, [Standards for Reporting EMG Data](https://isek.org/wp-content/uploads/2015/05/Standards-for-Reporting-EMG-Data.pdf), 1999, and the newer checklist [CEDE-Check](https://cede.isek.org/matrix/cede-check/).
- The steps from signal to model, and the fair split: Riascos Salas, Molinas and Lotte, [Machine learning methods for BCI](https://www.esann.org/sites/default/files/proceedings/2024/ES2024-4.pdf), 2024. It is about brain signals, and the same steps apply to muscle signals.
- Features and models: the [scikit-learn user guide](https://scikit-learn.org/stable/user_guide.html). Models for a microcontroller: [emlearn](https://emlearn.readthedocs.io/en/latest/).

## How to present it well
Write numbers, not adjectives. Give seconds, counts and file names. Use codes, never names.

## How to repeat our recording
Read `PROTOCOL.md`. It is enough to record the same way without asking us.

## Versions
Two versions are marked on GitHub: **First version** and **Report 1**. Open "Releases" on the right of the main page to see them with their dates.
