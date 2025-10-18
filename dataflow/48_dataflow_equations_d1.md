# Problem 48: Custom Dataflow Equation Design (Difficulty: d1)

## Problem Statement

Design dataflow equations for a new analysis that tracks "modified variables":

A variable is "modified" if it has been assigned to since the start of the current function, regardless of its original value.

```
B1:  x = input()
     y = 5              // y becomes modified
     z = x + y
     goto B2

B2:  if z > 10 goto B3 else goto B4

B3:  x = x + 1          // x becomes modified
     goto B5

B4:  // x remains unmodified in this path
     goto B5

B5:  w = x + y + z      // which variables are modified here?
     return w
```

## Tasks

1. **Design the dataflow framework** for "modified variables" analysis by defining:
   - Domain
   - Direction
   - Transfer function
   - Boundary conditions
   - Meet operator
   - Equations
   - Initialization

2. **Apply your framework** to the given code.

3. **Verify correctness** by checking your results make intuitive sense.

## Expected Output Format

- Complete framework definition
- Application to the example
- Discussion of analysis properties