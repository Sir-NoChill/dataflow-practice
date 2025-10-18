# Problem 36: Induction Variable Elimination (Difficulty: d4)

## Problem Statement

Eliminate unnecessary induction variables from complex loop patterns:

```c
int complex_loop(int n) {
    int sum = 0;
    int i = 0;          // basic induction variable
    int j = 0;          // derived: j = i
    int k = 10;         // derived: k = 10 + i
    int m = 0;          // derived: m = 2 * i

    while (i < n) {
        sum = sum + array[j] + array[k] + array[m];

        // All these update the same logical iteration
        i = i + 1;      // basic IV
        j = j + 1;      // same as i
        k = k + 1;      // 10 + i
        m = m + 2;      // 2 * i
    }

    return sum;
}
```

## Tasks

1. **Define induction variable analysis framework**:
   - How do you detect basic vs. derived induction variables?
   - What relationships exist between induction variables?
   - How do you verify that variables have linear relationships?

2. **Analyze induction variable relationships**:
   - Express each variable in terms of the basic induction variable
   - Identify which variables are redundant
   - Determine which variables can be eliminated

3. **Apply induction variable elimination**:
   - Choose which induction variables to keep
   - Transform uses of eliminated variables
   - Ensure loop termination conditions remain correct

4. **Show the optimized code** with minimal induction variables.

5. **Handle complex cases**: How would you handle:
   - Non-unit step sizes
   - Multiple basic induction variables
   - Conditional updates to induction variables

## Expected Output Format

- Induction variable relationship analysis
- Elimination strategy
- Transformed code with fewer induction variables
- Discussion of complex cases