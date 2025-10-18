# Problem 6: Live Variable Analysis with Phi Functions (SSA Form)

## Problem Statement
Perform live variable analysis on the following SSA-form Three Address Code containing phi functions.

## Three Address Code (SSA Form)
```
1:  x1 = 10
2:  y1 = 20
3:  if x1 > 5 goto 6
4:  z1 = x1 + y1
5:  goto 7
6:  z2 = x1 - y1
7:  z3 = φ(z1, z2)
8:  w1 = z3 * 2
9:  return w1
```

## Task
1. Explain how phi functions affect live variable analysis
2. Perform live variable analysis treating phi functions according to SSA semantics
3. Construct the interference graph considering phi function constraints
4. Identify opportunities for phi function elimination through register allocation

## Expected Output Format
- Explanation of phi function semantics in live variable analysis
- Live variable sets at each program point
- Interference graph with phi function considerations
- Analysis of register allocation implications for phi elimination