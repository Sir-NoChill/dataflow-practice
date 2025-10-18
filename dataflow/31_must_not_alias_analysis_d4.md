# Problem 31: Must-Not-Alias Analysis (Difficulty: d4)

## Problem Statement

Perform must-not-alias analysis to determine which pointers definitely do not alias:

```
B1:  x = malloc(sizeof(int))
     y = malloc(sizeof(int))
     z = malloc(sizeof(int))
     p = &local_var
     goto B2

B2:  if condition() goto B3 else goto B4

B3:  q = x
     r = y
     goto B5

B4:  q = y
     r = z
     goto B5

B5:  *q = 10
     *r = 20
     *p = 30
     if *q == *r goto B6 else goto B7

B6:  s = q    // s aliases q
     goto B8

B7:  s = &local_var2
     goto B8

B8:  *s = 40
     result = *x + *y + *z + *p
     return result
```

## Tasks

1. **Define must-not-alias analysis framework**:
   - How is this different from may-alias analysis?
   - What information can you derive when pointers must not alias?
   - How do you handle heap allocations vs. stack variables?

2. **Apply the analysis** to determine:
   - Which pointer pairs definitely do not alias?
   - How do different execution paths affect must-not-alias information?
   - What can be concluded about memory safety?

3. **Use must-not-alias information for optimization**:
   - Which memory operations can be reordered?
   - Where can redundant loads be eliminated?
   - Which pointer dereferences are guaranteed to access different memory?

4. **Handle uncertainty**: How does the analysis deal with:
   - Conditional pointer assignments
   - Unknown heap allocation behavior
   - Function calls that may return aliased pointers

5. **Optimization applications**: Show how must-not-alias enables specific optimizations.

## Expected Output Format

- Must-not-alias analysis framework
- Analysis results showing definite non-aliasing relationships
- Memory safety implications
- Specific optimization opportunities enabled by the analysis