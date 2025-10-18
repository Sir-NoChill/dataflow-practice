# Problem 8: Live Variables with Dead Code (Difficulty: d2)

## Problem Statement

Analyze the following TAC for live variables and identify dead code elimination opportunities:

```
B1:  x = 10
     y = x + 5
     z = y * 2
     w = z + x
     a = 100     // potentially dead?
     goto B2

B2:  b = x + y
     c = a + b   // uses a
     d = z * 3
     e = w + d
     unused = e * 2  // potentially dead?
     if b > 15 goto B3 else goto B4

B3:  f = x + z
     g = f * y
     h = 42      // potentially dead?
     goto B5

B4:  f = y + w
     i = f + e
     goto B5

B5:  result = f + e
     j = unused + h  // uses previously computed values
     return result
```

## Tasks

1. **Define the live variable framework** for this backward analysis.

2. **Apply live variable analysis** to completion.

3. **Identify dead code**:
   - Which assignments compute values that are never used?
   - Which variables are dead immediately after their definition?

4. **Dead code elimination**: Show the optimized code after removing dead assignments.

5. **Verify your optimization**: Confirm that removing the dead code doesn't change program semantics.

## Expected Output Format

- Complete live variable analysis
- List of dead assignments with justification
- Optimized TAC with dead code removed
- Brief verification that semantics are preserved