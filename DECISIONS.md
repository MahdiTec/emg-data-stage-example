# Decisions about what comes next (example)

For each part we write three short lines: what we, or our AI tool, chose. The reason, in our own words. What we still do not understand.
"Not decided yet" is allowed if we name the options. We choose with the training sessions only, and we open the test sessions once, at the end.

## 7. Features
**Chose.** Two numbers for each window of 0.25 s: the mean absolute value and the waveform length. Both measure the size of the signal. Our AI tool proposed them, and we checked them with a plot.
**Reason, in our own words.** In the plot of our first session, movement and rest sit apart on both. See `figures/two_features.png`.
**Not understood yet.** Would a feature about frequency add anything for two classes?
**Source.** Write here the page or paper where you found each feature.

## 8. Model
**Not decided yet.** We compare three kinds of model, from the simplest to the most flexible.

| Option | In plain words | What it keeps after training |
|---|---|---|
| One threshold | "movement if the size is above this number" | one number |
| Logistic regression | a straight border between the classes | a few numbers |
| Small decision tree | a short list of if rules | a few rules |

Our AI tool suggested the logistic regression.
**Reason, in our own words.** It said a straight border is enough for two classes that sit apart. We will check that against the single threshold.
**Not understood yet.** How it finds the border.
**Sources.** One for each option. Write them here.

## 9. Route
**Chose.** The model runs on our ESP32, as TinyML. A light shows the answer. After each measurement the board saves one record in a cloud service, the way a doctor saves the record of a patient: the date and time, the session, the code of the person, the features, and the answer of the model. First choice: Microsoft Azure. If no member can open an account there, ThingSpeak.
**Reason, in our own words.** The board answers fast and works without a computer.
**Proof.** The name of the board and its memory. A screenshot of the service that shows one saved record with its metadata, made with the account of a member.
**Not understood yet.** How the board sends a record, and how much one record can hold.
