# Problem 14: Conditional Constant Propagation with Loops (Difficulty: d3)

## Problem Statement

Convert the following code to TAC and perform conditional constant propagation:

```c
int analyze_loop(int input) {
    int x = 0;
    int y = input;
    int count = 0;

    while (count < 5) {
        if (y > 10) {
            x = x + 2;
            y = y - 3;
        } else {
            x = x + 1;
            y = y + 1;
        }
        count = count + 1;
    }

    if (x == 10) {
        return x + y;
    } else {
        return x * y;
    }
}
```

## Tasks

1. **Convert to TAC** with proper loop and conditional structure.

2. **Define the conditional constant propagation framework** with lattice operations.

3. **Handle the challenges of**:
   - Variable values that change in loops
   - How loop iterations affect constant propagation
   - Variables that may have different constant values on different paths

4. **Apply the analysis** showing how variable states evolve through loop iterations.

5. **Optimization analysis**:
   - Can any loop iterations be unrolled based on constant information?
   - Which conditional branches might be predictable?
   - What values could `input` have that lead to maximum optimization?

## Expected Output Format

- TAC representation with loop structure
- Complete lattice-based analysis through loop iterations
- Analysis of how different input values affect optimization potential
- Discussion of loop unrolling and branch elimination opportunities