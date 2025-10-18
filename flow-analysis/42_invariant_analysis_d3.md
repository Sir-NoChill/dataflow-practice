# Invariant Analysis

## Problem Statement
Detect and verify program invariants for optimization and correctness checking.

## Three-Address Code
```
B1: n = input_positive()     // Precondition: n > 0
    sum = 0                  // Invariant: sum >= 0
    i = 0                    // Invariant: 0 <= i <= n
    goto B2

B2: if i >= n goto B6       // Loop invariant: 0 <= i <= n, sum >= 0
B3: value = array[i]        // Precondition: 0 <= i < array_length
    if value >= 0 goto B4
    goto B5

B4: sum = sum + value       // Maintains: sum >= 0
    goto B5

B5: i = i + 1              // Maintains: i <= n
    goto B2

B6: average = sum / n       // Precondition: n > 0, Postcondition: average >= 0
    return average
```

## Tasks
1. Identify potential loop invariants and their domains
2. Verify invariant preservation through loop iterations
3. Use invariants to enable optimization (bounds check elimination, etc.)
4. Detect violated assumptions and potential errors
5. Generate assertion code for runtime invariant checking

## Expected Output Format
- Identified invariants with their validity domains
- Invariant preservation proof through loop body
- Optimization opportunities enabled by invariants
- Potential invariant violations and error conditions
- Generated assertion points for runtime verification