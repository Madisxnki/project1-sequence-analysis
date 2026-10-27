# Project 1: Identifying Mutations in NGS Data

## Purpose

The aim of this project is to use next generation sequencing of control and treated samples of Schizosaccharomyces pombe to identify any mismatches with the reference sequence. Mutation profiles can be studied and compared to see if there are differences in the number of mismatches between the two experimental groups.

## How to Run

Open Copy_of_C7147_Project_1_assessment.ipynb in Google Colab. Ensure that reads.csv is available at the file path used in the notebook. Run all cells in order to complete the final analysis.

## Inputs and Outputs

The reads.csv file contains the read ID, sample name, experimental group and DNA sequence for each read. These sequences are compared against a reference sequence to identify any mismatches.

The program provides read validation results, detected mutations, sample-level summaries, substitution counts and the three most frequently observed mismatch positions. It also compares mismatch frequencies between the control and treatment groups, reporting the mean percentages, differences between groups, Welch’s t-statistics and two-sided p-values.

## Code Design

Each element of validation, mutation detection, read analysis, sample summary and statistical analysis has been split into separate functions. This makes it easier to test and debug each part. Alternatively, all of these could be done in one function; however, this would make it harder to find any errors.

Dictionaries have been used to keep track of the number of substitutions and mismatches. This allows the counts to be updated directly using the type of mutation and reference position. This is better than continually searching through lists, which would require more comparisons.

Invalid reads have been included in the sample quality summary but not taken into account when calculating the mismatch rates so as not to reduce the frequency of mismatches. If there are no valid reads in a sample then the percentage of mismatches will be set to None.

## Testing

I can test the functions using small test datasets and assert statements. Comparing ACGA and ACGT shows that it correctly identifies that the fourth position has a mismatch. Testing with ACNT shows that it correctly logs invalid characters. Finally, testing with a dataset containing only ACNT shows that it correctly sets the percentage mismatch to None if there are no valid reads.

I also tested Step 5 with a control sample containing no valid reads. The test confirmed that the sample was excluded, the control mean and group difference were None, and unavailable statistical results were reported as N/A without an error.
