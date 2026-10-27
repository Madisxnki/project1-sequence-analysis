# Project 1 - NGS Sequence Mismatch Analysis

## Aim

This projects looks at NGS data from S. pombe to determine if there are differences in the frequency of DNA mismatches between samples in the treatments versus controls. We will also identify where mismatches have occurred in the genome.

## How to use

Use the assessment notebook on Google Colab. Upload the given reference sequence and reads.csv file. Use run all cells in order. There is no additional software needed.

## Input & Output

The program takes an input of a reference sequence of DNA and sequenced reads. The program checks that the length of reads and correct nucleotides are present. It also identifies substitutions and mismatch locations.

The output includes valid and invalid read counts, mismatch percentages, substitution frequencies, and frequently mismatched positions for each sample. Welch's t-tests compare mismatch frequencies between treatment and control groups at the three positions with the highest combined mismatch counts.

## Code Design

The code has been broken down into 5 parts so that each of these functions can be tested individually. This avoids any duplication of calculations.

Dictionaries have been used to store the number of substitutions and positions. This makes it easy to get the information using the mutation type and reference position. This was chosen instead of going through a list.

Invalid reads are still included in the quality summaries of the samples but are ignored when calculating the mismatch. This ensures that the percentage is not misleading. If there are no valid reads in the sample then a None value will be given for the mismatch.

Ties for the position with the most mismatches are resolved by taking the smallest reference position. This helps to ensure the values are ordered consistently.

## Testing

The program was tested using small data sets. Assert statements were used to ensure that the programs works correctly. This included testing with valid reads that had known mismatches, incorrect length sequences, invalid nucleotides and empty inputs. The summary functions will return empty collections and so this was tested with an empty input. A sample with no valid reads was tested to ensure that the mismatch percentage can handle undefined values safely.
