# Problem 5: Available Expressions with Function Calls (Difficulty: d2)

## Problem Statement

Analyze available expressions in the presence of function calls and array accesses:

```
B1:  t1 = a + b
     t2 = c * d
     x[0] = t1
     goto B2

B2:  t3 = a + b
     call foo(t2)
     t4 = c * d
     if t3 > 0 goto B3 else goto B4

B3:  t5 = x[0] + t4
     t6 = a + b
     goto B5

B4:  t7 = c * d
     t8 = a - b
     goto B5

B5:  t9 = a + b
     result = t9 + t8
     return result
```

## Tasks

1. **Define the available expressions framework** accounting for side effects.

2. **Consider the effects of**:
   - Function calls (assume `foo` may modify global variables)
   - Array/memory accesses
   - Which expressions are killed by these operations?

3. **Apply the analysis** with careful attention to how function calls affect expression availability.

4. **Discuss assumptions**: What assumptions did you make about the function `foo` and array `x`?

## Expected Output Format

- Framework definition with discussion of side effects
- Kill/Gen sets with justification for function call effects
- Complete iteration trace
- Discussion of assumptions and their impact on the analysis