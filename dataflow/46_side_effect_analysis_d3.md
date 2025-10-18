# Problem 46: Side Effect Analysis (Difficulty: d3)

## Problem Statement

Track side effects to enable optimizations:

```
B1:  x = pure_func(5)        // no side effects
     y = impure_func(x)      // has side effects
     z = another_pure(y)     // no side effects
     goto B2

B2:  if condition() goto B3 else goto B4

B3:  a = pure_func(5)        // same as x?
     b = impure_func(x)      // different from y?
     goto B5

B4:  c = another_pure(y)     // same as z?
     goto B5

B5:  result = a + b + c
     return result
```

## Tasks

1. **Define side effect analysis framework**.

2. **Track function purity** and side effect dependencies.

3. **Identify optimization opportunities** enabled by side effect information.

## Expected Output Format

- Side effect classification
- Dependency analysis
- Optimization opportunities