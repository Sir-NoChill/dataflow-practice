# Path-Sensitive Analysis

## Problem Statement
Implement path-sensitive analysis to improve precision over path-insensitive approaches.

## Three-Address Code
```
B1: flag = input_bool
    x = 0
    if flag goto B2
    goto B3
B2: x = 10
    y = x + 5          // y = 15 on this path
    goto B4
B3: x = 20
    y = x + 5          // y = 25 on this path
    goto B4
B4: if flag goto B5
    goto B6
B5: z = y - 10         // z = 5 if from B2
    result = z * 2     // result = 10 if from B2
    goto B7
B6: z = y - 15         // z = 10 if from B3
    result = z * 2     // result = 20 if from B3
    goto B7
B7: return result
```

## Tasks
1. Perform path-insensitive constant propagation analysis
2. Implement path-sensitive analysis tracking execution paths
3. Compare the precision of both approaches
4. Identify cases where path sensitivity enables better optimization
5. Analyze the computational complexity trade-offs

## Expected Output Format
- Path-insensitive analysis results with merged values
- Path-sensitive analysis with explicit path tracking
- Precision comparison showing additional constants discovered
- Optimization opportunities enabled by path sensitivity
- Complexity analysis and scalability considerations