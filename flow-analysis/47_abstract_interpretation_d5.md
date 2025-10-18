# Abstract Interpretation Framework

## Problem Statement
Design and implement an abstract interpretation framework for multiple concurrent analyses.

## Three-Address Code
```
B1: x = input_range(0, 100)    // x ∈ [0, 100]
    y = 0                      // y = 0
    ptr = &array[0]            // ptr points to array[0]
    goto B2

B2: if x <= 0 goto B6
B3: if x % 2 == 0 goto B4
    goto B5

B4: y = y + x                  // Even case
    x = x / 2
    ptr = ptr + 1
    goto B2

B5: y = y + x + 1             // Odd case
    x = (3 * x + 1) / 2
    ptr = ptr + 2
    goto B2

B6: *ptr = y
    return y
```

## Tasks
1. Design abstract domains for: ranges, points-to, and parity
2. Define abstract operations (join, meet, widening)
3. Implement the abstract interpreter with multiple domains
4. Handle domain interactions and reduced products
5. Analyze precision vs efficiency trade-offs

## Expected Output Format
- Abstract domain definitions and lattice structures
- Abstract operation implementations
- Multi-domain analysis results
- Domain interaction analysis (reduced products)
- Precision and efficiency evaluation