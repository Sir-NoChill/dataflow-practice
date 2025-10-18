# Problem 6: Available Expressions in Nested Loops (Difficulty: d3)

## Problem Statement

Convert the following nested loop structure to TAC and analyze available expressions:

```c
int compute(int n) {
    int sum = 0;
    for (int i = 0; i < n; i++) {
        int temp = i * 2;
        for (int j = 0; j < temp; j++) {
            sum = sum + (i * 2) + (j * 3);
            if (sum > 100) {
                sum = sum - (i * 2);
            }
        }
        sum = sum + (i * 2);
    }
    return sum + (n * 2);
}
```

## Tasks

1. **Convert to TAC** with proper basic block structure for nested loops.

2. **Draw the CFG** or provide a clear description showing loop nesting.

3. **Define available expressions framework** and identify all candidate expressions.

4. **Apply the analysis** paying attention to:
   - How loop back edges affect convergence
   - Which expressions remain available across loop iterations
   - The interaction between inner and outer loop expressions

5. **Optimization analysis**: Which expressions could be hoisted out of loops?

## Expected Output Format

- TAC with labeled basic blocks
- CFG description showing loop structure
- Complete analysis with multiple iterations until convergence
- List of expressions that could be loop-invariant and hoisted