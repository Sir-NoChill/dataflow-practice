# Problem 41: Type Inference Analysis (Difficulty: d3)

## Problem Statement

Perform type inference dataflow analysis on dynamically typed code:

```
B1:  x = 5        // x: int
     y = "hello"  // y: string
     goto B2

B2:  if condition() goto B3 else goto B4

B3:  x = 3.14    // x: float
     goto B5

B4:  x = true    // x: boolean
     goto B5

B5:  z = x + y   // type error?
     return z
```

## Tasks

1. **Define type inference framework** with lattice of types.

2. **Apply analysis** tracking type information flow.

3. **Identify type errors** where operations are invalid.

## Expected Output Format

- Type lattice definition
- Type inference results
- Error identification