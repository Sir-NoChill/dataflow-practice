# Problem 34: Loop Invariant Code Motion (Difficulty: d3)

## Problem Statement

Identify loop invariant expressions and optimize the following nested loop structure:

```c
int matrix_process(int n, int m, int constant) {
    int result = 0;
    int outer_invariant = constant * 2;

    for (int i = 0; i < n; i++) {
        int loop_variant = i * constant;
        int mixed_expr = outer_invariant + loop_variant;

        for (int j = 0; j < m; j++) {
            int inner_variant = j * i;
            int inner_invariant = constant + outer_invariant;
            result = result + inner_invariant + inner_variant;

            if (j % 2 == 0) {
                result = result + (constant * 2);  // same as outer_invariant
            }
        }

        result = result + mixed_expr;
    }

    return result + outer_invariant;
}
```

## Tasks

1. **Convert to TAC** preserving loop structure.

2. **Define loop invariant analysis**:
   - What makes an expression loop invariant?
   - How do you handle nested loops?
   - What safety conditions must be met for code motion?

3. **Identify invariant expressions** for each loop level:
   - Which expressions are invariant in the inner loop only?
   - Which expressions are invariant in both loops?
   - Which expressions depend on loop variables?

4. **Apply code motion optimization**:
   - Where should invariant expressions be moved?
   - How do you handle expressions used in conditionals?
   - Show the optimized code after hoisting.

5. **Analyze the benefits**: Calculate the reduction in operations achieved by the optimization.

## Expected Output Format

- TAC with nested loop structure
- Loop invariant analysis for each loop level
- Step-by-step code motion optimization
- Performance analysis of the optimization