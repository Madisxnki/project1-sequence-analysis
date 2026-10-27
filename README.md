# Project 1 - NGS Sequence Mismatch Analysis

## Aim

Analysis of NGS sequencing data from S. pombe to determine if there are differences in the frequency of DNA mismatches between the control and treatment samples. The code will identify any mismatches in the reference sequence.

## Usage

Open the assessment notebook on Google Colab, upload the reference sequence and reads.csv then run all cells in order. No extra software is needed for this.

## Input & Output

The program takes a reference DNA sequence and sequencing reads labelled by sample and experimental group. It checks read lengths and nucleotide validity, identifies substitutions, and records mismatch positions.

Results include counts of valid and invalid reads, mismatch percentages, substitution frequencies, and commonly mismatched positions for each sample. Welch’s t-tests compare mismatch frequencies between groups at the three positions with the highest combined mismatch counts.

## Code Design

Validation, mutation detection, read annotation, sample summarisation, and statistical comparison are separated into individual functions. This allows each stage to be tested independently and avoids repeated calculations. Combining everything into one function would make debugging more difficult.

Dictionaries are used to store the number of substitutions and positions. These allow us to directly look up each type of mutation and each position. This was chosen instead of searching through lists of mutation events which would have caused more comparisons.

Unreadable values are included in the summary but not counted in the mismatches. It is important that these are not included in the denominator as this would cause the percentage of mismatches to be lower than expected. If there are no valid values in the sample then the mismatch percentage will be set to None.

## Testing

The program was tested with small data sets and assert statements. We tested to see if a mismatch was added to position 4 when comparing the reads ACGA and ACGT. We also tested to see if any invalid nucleotide characters were found when comparing ACNT and ACGT. Lastly we tested to see if a sample with no valid values would have a mismatch percentage of None.
