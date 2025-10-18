# Problem 38: Sparse Conditional Constant Propagation (Difficulty: d4)

## Problem Statement

Apply sparse conditional constant propagation using SSA form:

```
// Convert this to SSA and apply sparse CCP
B1:  x = 5
     y = 10
     goto B2

B2:  if x > 3 goto B3 else goto B4

B3:  x = x + 1
     goto B5

B4:  x = 20
     goto B5

B5:  z = x + y
     if z > 15 goto B6 else goto B7

B6:  result = z * 2
     goto B8

B7:  result = z + 5
     goto B8

B8:  return result
```

## Tasks

1. **Convert to SSA form** with proper φ-function placement.

2. **Define sparse CCP framework** using SSA properties.

3. **Apply the algorithm** tracking which SSA values are constants vs. non-constants.

4. **Show optimization results** and compare with standard conditional constant propagation.

## Expected Output Format

- SSA conversion
- Sparse CCP analysis
- Comparison with dense analysis