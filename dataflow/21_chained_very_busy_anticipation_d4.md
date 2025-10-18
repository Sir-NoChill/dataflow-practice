# Problem 21: Chained Analysis - Very Busy + Anticipation for Code Motion (Difficulty: d4)

## Problem Statement

Use very busy expressions and anticipation analysis together to perform optimal code motion:

```
B1:  a = input()
     b = input()
     if a > 0 goto B2 else goto B6

B2:  if b > 0 goto B3 else goto B4

B3:  c = a + b
     d = a * b
     e = c + d
     goto B5

B4:  f = a - b
     g = a * b    // common with B3
     h = f + g
     goto B5

B5:  i = a + b    // appears in both paths eventually
     j = a * b    // appears in both paths
     result1 = i + j
     goto B7

B6:  k = a + 1
     if k > 5 goto B7 else goto B8

B7:  l = a + b    // will this be computed?
     m = a * b    // will this be computed?
     result2 = l + m
     goto B9

B8:  n = a - 1
     result3 = n
     goto B9

B9:  return result1 + result2 + result3
```

## Tasks

1. **Apply very busy expressions analysis** to identify expressions that will definitely be computed on all paths.

2. **Apply anticipation analysis** to identify expressions that will be computed later on all paths.

3. **Compare the results**:
   - Which expressions are both very busy AND anticipated?
   - How do the two analyses complement each other?
   - Which expressions are good candidates for early computation?

4. **Design code motion optimization**:
   - Which expressions should be moved earlier in the control flow?
   - Where is the optimal placement for moved expressions?
   - Show the code after applying code motion.

5. **Evaluate the optimization**:
   - How many redundant computations are eliminated?
   - Are there any trade-offs (e.g., increased register pressure)?

## Expected Output Format

- Very busy expressions analysis results
- Anticipation analysis results
- Comparison and intersection of results
- Code motion optimization plan
- Final optimized code with evaluation