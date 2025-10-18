# Sparse Analysis Techniques

## Problem Statement
Compare dense vs sparse approaches for conditional constant propagation on the following code.

## Three-Address Code
```
B1: x = 5
    y = 10
    z = input
    goto B2
B2: if x > 0 goto B3
    goto B7
B3: if y < 20 goto B4
    goto B5
B4: w = x + y
    x = x - 1
    goto B6
B5: w = x * y
    y = y + 1
    goto B6
B6: if z > w goto B7
    goto B2
B7: result = x + y + w
    return result
```

## Tasks
1. Implement dense conditional constant propagation with full lattice tracking
2. Implement sparse conditional constant propagation using SSA and def-use chains
3. Compare the computational complexity and precision
4. Analyze the sparse representation's effect on convergence speed
5. Evaluate memory usage differences between approaches

## Expected Output Format
- Dense algorithm implementation with full lattice states
- Sparse algorithm using SSA-based representation
- Step-by-step execution comparison
- Complexity analysis (time and space)
- Convergence speed and precision comparison
- Recommendations for different code characteristics