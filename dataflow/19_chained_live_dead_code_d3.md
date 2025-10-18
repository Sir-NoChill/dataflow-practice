# Problem 19: Chained Analysis - Live Variables + Dead Code Elimination (Difficulty: d3)

## Problem Statement

Apply live variable analysis followed by dead code elimination on the following TAC:

```
B1:  a = input()
     b = a + 10
     c = b * 2      // potentially dead
     d = a + 5
     e = b + d
     unused1 = c + e  // potentially dead
     goto B2

B2:  if a > 0 goto B3 else goto B4

B3:  f = b + d
     g = f * 3
     temp1 = e + g    // potentially dead
     h = f + 2
     goto B5

B4:  i = d + 1
     j = i * b
     temp2 = e * i    // potentially dead
     k = j - 1
     goto B5

B5:  result = f + k  // f may be undefined on one path!
     temp3 = unused1 + temp1  // multiple potentially dead vars
     return result
```

## Tasks

1. **Apply live variable analysis** to determine which variables are live at each program point.

2. **Identify the problem**: Notice that variable `f` is used in B5 but may not be defined on all paths. How does this affect the analysis?

3. **Perform dead code elimination** based on liveness information:
   - Which assignments are dead?
   - Which variables are never used after definition?

4. **Fix the undefined variable issue**: Propose a solution for the `f` variable problem in B5.

5. **Iterative improvement**: After dead code elimination, would re-running live variable analysis reveal additional optimization opportunities?

## Expected Output Format

- Complete live variable analysis
- Identification of the undefined variable problem
- Dead code elimination results
- Proposed fix for undefined variables
- Discussion of iterative optimization benefits