# Induction Variable Analysis

## Problem Statement
Analyze the following nested loop code to identify induction variables and their relationships.

## Three-Address Code
```
B1: i = 0
    k = 0
    goto B2
B2: if i >= 100 goto B7
B3: j = i * 2
    l = k + 5
    goto B4
B4: if j >= 200 goto B6
B5: arr[j] = l
    j = j + 2
    l = l + 10
    goto B4
B6: i = i + 1
    k = k + 5
    goto B2
B7: return
```

## Tasks
1. Identify all induction variables in each loop
2. Classify variables as basic or derived induction variables
3. Determine the relationships between derived and basic induction variables
4. Analyze the strength of induction relationships
5. Identify opportunities for induction variable elimination

## Expected Output Format
- Loop structure analysis
- Classification of each variable (basic IV, derived IV, or loop invariant)
- Mathematical relationships for derived induction variables
- Strength analysis (linear, quadratic, etc.)
- Candidates for induction variable elimination or strength reduction