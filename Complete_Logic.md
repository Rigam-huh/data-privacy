
# libraries 
 
import pandas as pd
import numpy as np

-------------------------------------------------------------------------------------------------------------------------------------------------------------
# reading data from csv files

original_df = pd.read_csv(r"C:\Users\Rigam\Desktop\numerical_analysis\data-challenge-original.csv")
protected_df = pd.read_csv(r"C:\Users\Rigam\Desktop\numerical_analysis\protected_data_challenge.csv")

- here the original or decrypted dataset is read in orignal_df
- here the protected or encrypted dataset is read in protected_df
-------------------------------------------------------------------------------------------------------------------------------------------------------------
# selecting column ratios

ratio_columns = [
    "Groceries", "Transport", "Healthcare", "Utilities",
    "Insurance", "Eating_Out", "Entertainment", "Rent"
]

- The idea is to compare spending patterns normalized by income.
--------------------------------------------------------------------------------------------------------------------------------------------------------------
# filtering columns that exists

valid_ratios = [col for col in ratio_columns if col in protected_df.columns and col in original_df.columns]

--------------------------------------------------------------------------------------------------------------------------------------------------------------
# creating new ratio columns

protected_df[f"{col}_to_income"] = protected_df[col] / protected_df["Income"]
original_df[f"{col}_to_income"] = original_df[col] / original_df["Income"]

- For each valid expense column:
    * It creates a new column like Groceries_to_income, Rent_to_income, etc.
- These new columns represent how much each person spends relative to their income.

--------------------------------------------------------------------------------------------------------------------------------------------------------------
# Defining the Matching Logic

def rows_match(prot_row, orig_row, ratio_tolerance=0.15):

- Key function: Compares a protected row and an original row.
- The logic:
    - For each expense ratio column, check if values are "close enough" (rtol=0.15 means ±15% relative difference).
    - Also ensures:
        * Occupation matches exactly.
        * City_Tier matches exactly.
- If any check fails → returns False, otherwise → True.

--------------------------------------------------------------------------------------------------------------------------------------------------------------
# Finding Matches

for i, prot_row in protected_df.iterrows():
    for j, orig_row in original_df.iterrows():
        if rows_match(prot_row, orig_row):
            matches.append({...})
            break

- Nested loop:
    - For every row in protected_df, it tries to find a matching row in original_df.
    - As soon as a match is found, it records the pair and breaks (no multiple matches for the same protected record).
- It stores:
    - Indices
    - Identifiers
    - Names from both datasets

--------------------------------------------------------------------------------------------------------------------------------------------------------------
# Creating a Final DataFrame

matches_df = pd.DataFrame(mathces)
print("Total Matches Found:", len(matches-df))
matches_df

- It tries to create a new dataframe of matches and print the total number.
--------------------------------------------------------------------------------------------------------------------------------------------------------------
