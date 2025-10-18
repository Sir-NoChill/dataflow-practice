# Iterative Dataflow Framework Implementation

## Problem Statement
Implement the iterative dataflow framework to solve reaching definitions and available expressions simultaneously.

## Three-Address Code
```
B1: x = a + b
    y = c * d
    goto B2
B2: if condition goto B3
    goto B4
B3: x = x + 1
    z = x * y
    goto B5
B4: y = y - 1
    z = a + b
    goto B5
B5: if z > 10 goto B6
    goto B7
B6: x = z / 2
    goto B2
B7: return x + y + z
```

## Tasks
1. Define transfer functions for both reaching definitions and available expressions
2. Set up the iterative algorithm with proper initialization
3. Show the step-by-step evolution of dataflow sets through iterations
4. Demonstrate convergence and fixed-point detection
5. Analyze the interaction effects when running multiple analyses

## Expected Output Format
- Transfer function definitions for each analysis
- Initial dataflow set values
- Iteration-by-iteration dataflow set evolution
- Convergence analysis and fixed-point identification
- Discussion of analysis interaction and computational complexity