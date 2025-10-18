# Problem 3: Reaching Definitions with Complex Control Flow (Difficulty: d2)

## Problem Statement

Analyze the following TAC with nested conditionals and multiple variable redefinitions:

```
B1:  a = 10
     b = 20
     c = a + b
     if c > 25 goto B2 else goto B3

B2:  a = a * 2
     if a > 30 goto B4 else goto B5

B3:  b = b / 2
     c = a - b
     goto B5

B4:  c = a + 100
     a = c - b
     goto B6

B5:  a = b + c
     b = a * 3
     goto B6

B6:  d = a + b + c
     if d > 100 goto B7 else goto B8

B7:  a = 0
     b = 0
     goto B8

B8:  result = a + b + c + d
     return result
```

## Tasks

1. **Define the reaching definitions framework** with all required components.

2. **Identify kill and gen sets** for each basic block explicitly.

3. **Apply the iterative algorithm** showing at least the first 3 iterations and the final converged state.

4. **Answer specific questions**:
   - Which definitions of variable `a` reach the assignment `result = a + b + c + d`?
   - Are there any unreachable definitions? Why?
   - Which basic block has the most complex IN set and why?

## Expected Output Format

- Kill and Gen sets for each basic block
- Iteration-by-iteration IN/OUT sets
- Answers to the specific questions with justification