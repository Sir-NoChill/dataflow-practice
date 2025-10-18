# Problem 20: Chained Analysis - Constant Propagation + Available Expressions (Difficulty: d4)

## Problem Statement

Apply conditional constant propagation followed by available expressions analysis to maximize optimization opportunities:

```
B1:  x = 5
     y = 10
     z = x + y    // constant foldable
     if x > 3 goto B2 else goto B3  // predictable branch

B2:  a = x * 2   // constant foldable
     b = y + z   // constant foldable
     c = a + b   // constant foldable
     goto B4

B3:  // unreachable due to constant condition
     a = 20
     b = 30
     c = a + b
     goto B4

B4:  d = a + b   // available expression?
     e = x + y   // same as z?
     f = x * 2   // same as a?
     result = d + e + f
     return result
```

## Tasks

1. **Apply conditional constant propagation** first:
   - Determine which variables have constant values
   - Identify which branches are unreachable
   - Perform constant folding

2. **Transform the code** based on constant propagation results:
   - Replace variables with constants where possible
   - Eliminate unreachable code
   - Simplify conditional branches

3. **Apply available expressions analysis** to the transformed code:
   - Which expressions are now available after constant propagation?
   - How does constant propagation affect expression availability?

4. **Perform expression optimization**:
   - Eliminate redundant expressions
   - Introduce temporary variables for common subexpressions

5. **Analyze the synergy**: How do the two optimizations work together to produce better results than either alone?

## Expected Output Format

- Step 1: Conditional constant propagation results
- Step 2: Code after constant propagation and folding
- Step 3: Available expressions analysis on transformed code
- Step 4: Final optimized code
- Discussion of optimization synergy effects