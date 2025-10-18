# Problem 11: Very Busy Expressions with Exception Handling (Difficulty: d3)

## Problem Statement

Analyze very busy expressions in code with exception handling constructs:

```
B1:  x = input()
     y = x + 10
     try_start
     goto B2

B2:  a = x * y
     b = divide(a, x)  // may throw exception
     c = x * y
     goto B3

B3:  d = x + 10
     e = x * y
     try_end
     goto B5

B4:  // exception handler
     catch_start
     f = x + 10
     g = error_value()
     h = x * y
     catch_end
     goto B5

B5:  result = x + 10
     final = x * y
     return result + final
```

## Tasks

1. **Model exception control flow**: How do exception edges affect the CFG?

2. **Define very busy expressions framework** accounting for exception paths.

3. **Consider the effects of**:
   - Expressions that may not execute due to exceptions
   - How exception handlers affect expression "busyness"
   - The relationship between try blocks and catch blocks

4. **Apply the analysis** with careful attention to exception control flow.

5. **Optimization discussion**: Which expressions can be safely moved despite exception possibilities?

## Expected Output Format

- CFG description including exception edges
- Framework definition with exception considerations
- Complete analysis results
- Discussion of safe code motion in presence of exceptions