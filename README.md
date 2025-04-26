# data-privacy
here is the complete analysis of the code used in the process of decrypting the given protected data

# Markdown File for Matching Protected and Unprotected Data

# Problem Statement
This challenge presents a crucial problem at the intersection of data science and privacy: How can we preserve useful patterns in data for research purposes without compromising the privacy of individuals? While ensuring utility is essential, designing privacy protections robust enough to withstand attacks from skilled adversaries remains an ongoing challenge—and that’s where your expertise comes in.

As part of the challenge, we have provided the following materials to help you get started:

Original Data Set

Private Data Set

Challenge Guide Document

We encourage you to carefully review the guide before beginning your work.

# Author
- Rigam Bhaduri
- Sabayasachi Mukhopadhyay 
- Amrita Debnath
- Soumyashree Ghosh

# program logic
This program compares two datasets (`original_df` and `protected_df`) to find matching records based on:
- Expense-to-income ratios (8 categories)
- Occupation
- City tier

## Code Structure

### Initial Setup
import pandas as pd
import numpy as np

#### What Has Been Completed
✅ Imported necessary libraries (pandas, numpy).

✅ Loaded the original and protected datasets.

✅ Selected and verified important columns (Groceries, Transport, etc.).

✅ Created new ratio columns (e.g., Groceries_to_income) to normalize expenses.

✅ Developed two versions of the matching logic:

Old version: Brute-force nested loop (O(n²)) — correct but slow.

Optimized version: Using dictionary hashing to achieve fast (O(n)) matching.

✅ Found matching rows and collected them into a new DataFrame (matches_df).

✅ Saved the matched results into a CSV file (out.csv).

✅ Performed frequency analysis on the Original_Name column.

✅ Planned and almost saved frequency counts into a separate CSV file.



