# SSA Form: φ-function Placement

## Problem Statement
Given the following three-address code and its dominance frontiers, place φ-functions to convert to minimal SSA form.

## Three-Address Code
```
B1: x = 1
    y = 2
    goto B2
B2: if condition goto B3
    goto B4
B3: x = x + 1
    z = x * 2
    goto B5
B4: y = y + 1
    z = y * 3
    goto B5
B5: w = x + y + z
    if w > 10 goto B6
    goto B7
B6: x = w - 5
    goto B5
B7: return w
```

## Given Information
- DF(B1) = {}
- DF(B2) = {}
- DF(B3) = {B5}
- DF(B4) = {B5}
- DF(B5) = {B5}
- DF(B6) = {B5}
- DF(B7) = {}

## Tasks
1. Determine which variables need φ-functions at which join points
2. Place φ-functions in the correct basic blocks
3. Apply the iterated dominance frontier algorithm
4. Show the code after φ-function insertion but before renaming

## Expected Output Format
- Analysis of variable definitions and their dominance frontiers
- φ-function placement for each variable
- Modified basic blocks with φ-functions inserted
- Verification that minimal SSA property is satisfied