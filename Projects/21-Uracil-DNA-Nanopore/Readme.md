# Detecting Uracil in DNA from Nanopore Signals

## Background

A nanopore sequencer reads DNA by feeding a single strand through a tiny pore and
recording an electrical current as it passes. The setup is the following: a
membrane separates two chambers, a single pore sits in the membrane, and a voltage
across it drives a steady current of ions through the pore. When a motor protein
feeds a DNA strand through, the strand partly blocks the pore and changes that
current. The result is a signal that traces how the current rises and falls over
time as the strand moves along.

DNA is a chain of bases, and the pore is bigger than a base, so it can hold several bases at once. The current at any moment is affected by
multiple bases at the same time. It depends on a short stretch of the sequence sitting in the pore together, plus a fair amount of noise.
Turning that signal back into the actual sequence of letters is called
*basecalling*, and a software with a neural network based approach does it very
accurately.

## Uracil in the DNA

DNA is normally made of four bases: adenine (A), cytosine (C),
guanine (G), and thymine (T). In some cases slightly different alternative bases
appear. This exercise is about uracil (U), which is almost identical to T and could
replace it in the DNA. In living cells, U ends up in DNA either by accident, or on 
purpose, as a signal tied to processes like gene regulation and the immune system's 
antibody production. Currently, basecalling softwares just read a U as an ordinary 
T and never notice it.

A U should perturb the current in a slightly different way than a T would. The whole
question is whether that difference is large enough to spot against all the noise.

## Tasks

Standard tools won't flag U. Your job is to figure out whether the signal actually
contains enough information to tell the two apart, and if it does, to build a model
that can make that call.

- Explore the normalized nanopore signal data from two datasets: one with DNA that
  has only T alongside the other three bases, and one with DNA where all Ts were
  replaced with U.
- Compare the electrical signal from each dataset, finding the subtle differences
  between T and U signals.
- Build an XGBoost model that predicts, for a given T position, whether it's a T or a U.
- Measure the performance of your model on the provided test data.