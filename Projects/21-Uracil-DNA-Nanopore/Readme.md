# Detecting Uracil in DNA from Nanopore Signals


## Background

A nanopore sequencer reads DNA by feeding a single strand through a tiny pore and
recording an electrical current as it passes. The setup is the following: a
membrane separates two chambers, a single pore sits in the membrane, and a voltage
across it drives a steady current of ions through the pore. When a motor protein
feeds a DNA strand through, the strand partly blocks the pore and changes that
current. The result is a signal that traces how the current rises and falls over
time as the strand moves along.

DNA is a chain of bases, and the pore is bigger than
one of them, so it holds several at once. So the
current at any moment doesn't depend on a single base. It depends on a short
stretch of the sequence sitting in the pore together, plus a fair amount of noise.
Turning that signal back into the actual sequence of letters is called
*basecalling*, and a software with a neural network based approach does it very
accurately.

Read more — how nanopore sequencing works:
https://nanoporetech.com/platform/technology · how basecalling works:
https://nanoporetech.com/platform/technology/basecalling

## Uracil in the DNA

DNA is normally made of four bases: adenine (A), cytosine (C),
guanine (G), and thymine (T). In some cases slightly different alternative bases
appear. This exercise is about uracil (U), which is almost identical to T and could
replace it in the DNA. In living cells, U ends up in DNA either by accident, or on 
purpose, as a signal tied to processes like gene regulation and the immune system's 
antibody production. The standard basecalling software just reads a U as an ordinary 
T and never notices.

A U should disturb the current a little differently than a T would. The whole
question is whether that difference is big enough to spot against all the noise.

## Tasks

Standard tools won't flag U. Your job is to figure out whether the signal actually
contains enough information to tell the two apart, and if it does, to build a model
that can make that call.

- Explore the normalized nanopore signal data from two datasets: one with DNA that
  has only T alongside the other three bases, and one with DNA where all Ts were
  replaced with U.
- Compare the electrical signal from each dataset — for example, plot the
  distribution of `trimmmean` for T versus U at a few positions and see whether
  the shift is visible by eye.
- Build an XGBoost model that predicts, for a given T position, whether it's a T or a U.
- Measure the performance of your model on the provided test data.

## The data

You get two datasets. In both, the raw nanopore signal has already been turned into
a table of numbers, so you don't work with the signal directly. The reads are all
forward-strand (see the note below on why).

- **control**: DNA where the T positions are real T.
- **modified**: the same DNA, but every T is replaced by U.

Each row is one position in one read. It says how the current behaved while that
position was in the middle of the pore. For each position you get three numbers, all from the
normalized signal:

- **trimmed mean** — the average current at the position. This is the main thing
  that should differ between T and U.
- **trimmed standard deviation** — how much the current wobbles at the position.
- **dwell time** — how long the position stayed in the pore.

("Trimmed" means a few extreme samples are dropped first, so spikes don't skew the
number.)

The table has these columns:

| column | meaning |
|---|---|
| `ref_name` | the reference sequence the read was aligned to |
| `sample` | `Control` (T) or `Modified` (U) — this is the label to predict |
| `read_id` | the individual read |
| `ref_pos` | position along the reference |
| `ref_base` | the base at that position |
| `dwell` | dwell time (number of signal samples) |
| `trimmmean` | trimmed mean of the normalized current |
| `trimsd` | trimmed standard deviation of the current |


A few things to keep in mind:

- **Only T positions matter.** U only ever replaces T, so the question is always:
  at this T, is it a real T or a hidden U?
- **You only get forward-strand reads.** The labels come from the reference
  sequence — it tells you the true base at each position — and the reference matches
  the forward strand. A forward read lines up with it base-for-base, so each signal
  value can be tied to the correct reference base. A reverse read is the reverse
  complement, so it doesn't line up with the reference the same way and can't be
  labelled from it directly. That's why only the forward reads are shared.
- **Each position in the reference is measured many times.** Every read that covers a position gives
  its own measurement, so the same position shows up in many rows — one row per
  read. You can treat each row (one read at one position) as its own example, or
  average all the reads at a position into a single row and use that.

The metrics were extracted with the Remora API
(https://github.com/nanoporetech/remora): the signal was mapped to the
reference, normalized with a k-mer level model, and summarized into the three
numbers above.

The control and modified sets above are your **training data**. You also get a
separate **test dataset** in the same format — use it only to measure your final
performance, not for training or tuning.

## Building the model

The model is a two-class problem: at each T position, is it a real T or a U?

- **Keep only the T positions** (`ref_base` is T).
- **Label** each one: control is a T (0), modified is a U (1).
- **Use the three metrics** as features — `trimmean`, `trimsd` and `dwell`.
- **Train an XGBoost classifier** on the training data.
- **Measure it on the test dataset** — accuracy, precision, recall, AUROC, and the
  confusion matrix.

XGBoost is a good starting point, but you can try other classifiers too (for
example logistic regression, a random forest, or a small neural network) and
compare how they do.
  replaced with U.
- Compare the electrical signal from each dataset, finding the subtle differences
  between T and U signals.
- Build an XGBoost model that predicts, for a given T position, whether it's a T or a U.
- Measure the performance of your model on the provided test data.
