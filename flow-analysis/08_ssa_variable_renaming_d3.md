# SSA Form: Variable Renaming

## Problem Statement
Complete the SSA transformation by performing variable renaming on the code with φ-functions already placed.

## Three-Address Code with φ-functions
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
B5: x = φ(x, x, x)  // from B3, B4, B6
    y = φ(y, y)      // from B3, B4
    z = φ(z, z)      // from B3, B4
    w = x + y + z
    if w > 10 goto B6
    goto B7
B6: x = w - 5
    goto B5
B7: return w
```

## Tasks
1. Perform variable renaming to create unique names for each definition
2. Update φ-function arguments with correct variable versions
3. Ensure each use refers to the correct definition
4. Maintain proper SSA form throughout the transformation

## Expected Output Format
- Complete SSA form with renamed variables
- Mapping of original variables to their SSA versions
- Updated φ-functions with correct arguments
- Verification that SSA properties are satisfied