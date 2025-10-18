# Problem 49: Bidirectional Dataflow Analysis (Difficulty: d4)

## Problem Statement

Design and apply a bidirectional analysis that combines forward constant propagation with backward dead code information:

```
B1:  x = 5
     y = 10
     z = x + y          // can be folded to 15
     dead_var = 999     // never used
     goto B2

B2:  if x > 3 goto B3 else goto B4

B3:  a = z * 2          // z is constant, so a = 30
     unused = a + 100   // never used
     goto B5

B4:  a = 20
     temp = z + 1       // never used
     goto B5

B5:  result = a         // a has different values from different paths
     return result
```

## Tasks

1. **Design a bidirectional framework** that:
   - Propagates constants forward
   - Propagates liveness information backward
   - Uses both to maximize optimization

2. **Apply the analysis** showing how forward and backward information interact.

3. **Optimize the code** using both types of information.

4. **Compare with sequential analysis**: How does bidirectional analysis improve results?

## Expected Output Format

- Bidirectional framework design
- Forward and backward analysis results
- Combined optimization strategy
- Comparison with sequential approaches