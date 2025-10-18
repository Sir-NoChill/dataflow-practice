# Problem 12: Very Busy Expressions in Complex Loop Nest (Difficulty: d4)

## Problem Statement

Convert the following complex nested structure to TAC and analyze very busy expressions:

```c
int matrix_compute(int n, int m) {
    int sum = 0;
    int factor = n + m;

    for (int i = 0; i < n; i++) {
        int outer_temp = i * factor;

        for (int j = 0; j < m; j++) {
            int inner_temp = j * factor;
            sum = sum + (outer_temp + inner_temp);

            if ((i + j) % 2 == 0) {
                sum = sum + (n + m);
            } else {
                sum = sum - (n + m);
            }
        }

        sum = sum * (n + m);
    }

    return sum + (n + m);
}
```

## Tasks

1. **Convert to TAC** preserving loop structure and expression relationships.

2. **Construct detailed CFG** showing nested loop back edges and conditional branches.

3. **Apply very busy expressions analysis** with attention to:
   - How nested loops affect expression busyness
   - Which expressions are busy across multiple loop levels
   - The interaction between conditional branches and loop iterations

4. **Advanced optimization analysis**:
   - Which expressions could be hoisted to outer loops?
   - Which expressions are busy enough to warrant code motion?
   - How do the nested conditionals affect optimization opportunities?

5. **Performance impact**: Estimate the performance improvement from optimizing very busy expressions.

## Expected Output Format

- Detailed TAC with nested loop structure
- Complete CFG description
- Full analysis with multiple iterations until convergence
- Comprehensive optimization recommendations with performance analysis