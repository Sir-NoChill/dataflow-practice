# Problem 2: Reaching Definitions with Loops (Difficulty: d1)

## Problem Statement

Convert the following source code to Three Address Code and perform reaching definitions analysis.

```c
int x = 0;
int y = 1;
while (x < 10) {
    x = x + y;
    if (x % 2 == 0) {
        y = y * 2;
    } else {
        y = y + 1;
    }
}
return x + y;
```

## Tasks

1. **Convert to TAC**: Transform the source code into Three Address Code with appropriate basic blocks.

2. **Define the dataflow framework** for reaching definitions analysis.

3. **Construct the CFG**: Draw or describe the control flow graph showing all basic blocks and edges.

4. **Apply reaching definitions analysis** using the iterative algorithm, paying special attention to how the loop affects convergence.

5. **Identify interesting cases**: Note any definitions that reach multiple points or are killed and redefined.

## Expected Output Format

- TAC representation with labeled basic blocks
- CFG description
- Complete IN/OUT sets for each iteration until convergence
- Brief analysis of which definitions reach the return statement