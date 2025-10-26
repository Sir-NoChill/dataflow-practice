# Problem 4: Basic Available Expressions Analysis (Difficulty: d1)

## Problem Statement

Given the following TAC, perform available expressions analysis to identify common subexpressions:

```
B1:  a = x + y
     b = x * z
     c = x + y
     if a > 10 goto B2 else goto B3

B2:  d = x + y
     e = z * 2
     goto B4

B3:  f = x * z
     g = y + z
     goto B4

B4:  h = x + y
     i = x * z
     return h + i
```

## Tasks

1. **Define the available expressions framework** by specifying:
   - The domain of the analysis
     - The set of all expressions
   - The direction of the analysis
     - Forward
   - The generalized transfer function
     - `OUT[B] = f_B(IN[B])`
   - The boundary value
     - `OUT[START] = { }`
   - The meet operator
     - Set Intersection
   - The dataflow equation
     - `OUT[B] = gen[B] U (IN[B] - kill[B])`
     - `IN[B] = \bigcap_{P \in pred(B)} IN[P]`
   - The initialization of nodes
     - `OUT[B] = { }`

2. **Identify all expressions** in the program that could be available.
   - `x * z`
   - `x + y`
   - `z * 2`
   - `y + z`
   - `h + i`

3. **Compute kill and gen sets** for each basic block.

   - We will use a bitvector notation to denote the available expressions at any
     given point. The bit-vector notation is as follows:

     `x * z | x + y | z * 2 | y + z | h + i`

     where the pipe operator (`|`) denotes the boundary between bits.
   - Now we can compute the gen and kill sets for each basic block:

     | Basic Block | Gen   | Kill   |
     | ----------- | ----- | ------ |
     | START       | 00000 | 00000 |
     | B1          | 11000 | 00000 |
     | B2          | 01100 | 00000 |
     | B3          | 10010 | 00000 |
     | B4          | 11001 | 00001 |

4. **Apply the iterative algorithm** until convergence.

   - First we need to construct the CFG for the program:
     ```mermaid
     graph TD
         START --> B1
         B1 --> B2
         B1 --> B3
         B2 --> B4
         B3 --> B4
     ```

   - Now we can apply the iterative algorithm directly:

     | Block | IN    | OUT   |
     | ----- | ----- | ----- |
     | START | 00000 | 00000 |
     | B1    | 00000 | 11000 |
     | B2    | 00000 | 01100 |
     | B3    | 00000 | 00010 |
     | B4    | 00000 | 01001 |
     | END   | 00000 | 00000 |
     | START | 00000 | 00000 |
     | B1    | 00000 | 11000 |
     | B2    | 00000 | 01100 |
     | B3    | 00000 | 00010 |
     | B4    | 00000 | 01001 |
     | END   | 00000 | 00000 |
     | START | 00000 | 00000 |
     | B1    | 00000 | 11000 |
     | B2    | 11000 | 11100 |
     | B3    | 11000 | 11010 |
     | B4    | 11000 | 11001 |
     | END   | 11001 | 11001 |
     | START | 00000 | 00000 |
     | B1    | 00000 | 11000 |
     | B2    | 11000 | 11100 |
     | B3    | 11000 | 11010 |
     | B4    | 11000 | 11001 |
     | END   | 11001 | 11001 |


   - The algorithm converges after 3 iterations. Note that we consider `START`
     specially, since it does not contribute to the available expressions.


5. **Identify optimization opportunities**: Which expressions are redundant and could be eliminated?
    - We can pre-compute all expressions, however pre-computing expressions 1,
      2 and 5 offer the most tangible benefit as we cannot know at compile time
      if BB2 or BB3 will be executed.
    - Since the entire program returns expression 5, we can simply compute i
      with the equation `i = x * z; h = x + y` and then hoist both, allowing us
      to return `h + i` before executing control flow at all.

## Expected Output Format

- List of all expressions considered
- Kill and Gen sets for each basic block
- IN/OUT sets for each iteration
- List of redundant expressions that could be optimized
