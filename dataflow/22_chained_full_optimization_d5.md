# Problem 22: Complete Optimization Pipeline (Difficulty: d5)

## Problem Statement

Apply a complete sequence of dataflow analyses to achieve maximum optimization on the following code:

```c
int optimize_me(int x, int y) {
    int a = x + y;
    int b = 10;
    int c = a + b;
    int dead_var = 999;  // never used

    if (x > 5) {
        int d = x + y;   // same as a
        int e = d + b;   // same as c
        int f = e * 2;
        dead_var = f;    // overwrites dead_var
        return f + c;
    } else {
        int g = a + b;   // same as c
        int h = g + 10;
        int i = x + y;   // same as a
        return h + i;
    }
}
```

## Tasks

1. **Convert to TAC** with proper basic block structure.

2. **Apply the following analyses in sequence**:
   a. Reaching definitions
   b. Live variable analysis
   c. Available expressions
   d. Conditional constant propagation (assume x=6 for one scenario)
   e. Very busy expressions
   f. Dead code elimination

3. **After each analysis**, show:
   - The analysis results
   - What optimizations are enabled
   - The transformed code

4. **Demonstrate optimization interactions**:
   - How does dead code elimination affect available expressions?
   - How does constant propagation enable further optimizations?
   - Which analyses need to be re-run after code transformations?

5. **Final evaluation**:
   - Compare the original vs. fully optimized code
   - Count the number of operations eliminated
   - Discuss any remaining optimization opportunities

## Expected Output Format

- Original TAC
- Step-by-step analysis and optimization results
- Intermediate code after each optimization
- Final optimized code
- Comprehensive evaluation of optimization effectiveness