# Problem 9: Live Variables in Loop with Multiple Exits (Difficulty: d3)

## Problem Statement

Convert the following code to TAC and perform live variable analysis:

```c
int process(int n) {
    int x = n;
    int y = 0;
    int z = 1;

    while (x > 0) {
        y = y + x;
        z = z * 2;
        x = x - 1;

        if (y > 100) {
            break;  // early exit
        }

        if (z > 50) {
            x = 0;  // another way to exit
        }
    }

    int result = y + z;
    return result;
}
```

## Tasks

1. **Convert to TAC** with proper handling of loop exits and break statements.

2. **Draw the CFG** showing all possible control flow paths including early exits.

3. **Define and apply live variable analysis** with attention to:
   - How multiple loop exits affect liveness
   - Which variables remain live across different exit paths
   - The convergence behavior with multiple back edges

4. **Register pressure analysis**:
   - What is the maximum number of simultaneously live variables?
   - Where in the loop does register pressure peak?

5. **Optimization opportunities**: Which variables could be eliminated or have their lifetimes shortened?

## Expected Output Format

- TAC with labeled basic blocks
- CFG description
- Complete live variable analysis showing convergence
- Register pressure analysis at key program points
- Discussion of optimization opportunities