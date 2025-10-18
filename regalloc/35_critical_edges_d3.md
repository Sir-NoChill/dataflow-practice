# Problem 35: Critical Edge Splitting for Register Allocation

## Problem Statement
Handle critical edges in the control flow graph that complicate register allocation and phi elimination.

## Three Address Code (SSA Form)
```
1:  x = 10
2:  y = 20
3:  if x > 5 goto 6
4:  z1 = y + 1
5:  goto 8
6:  if y > 15 goto 8
7:  z2 = y - 1
8:  z3 = φ(z1, z2, y)   // phi with multiple predecessors
9:  result = z3 * 2
10: return result
```

## Task
1. Draw the control flow graph and identify critical edges
2. Explain why critical edges complicate phi function elimination
3. Apply critical edge splitting to resolve the complications
4. Show how phi elimination works after critical edge splitting
5. Perform register allocation on the transformed code

## Expected Output Format
- Control flow graph with critical edges identified
- Explanation of phi elimination complications
- Critical edge splitting transformation
- Modified CFG and TAC after splitting
- Register allocation on the transformed code