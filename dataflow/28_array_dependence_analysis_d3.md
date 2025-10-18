# Problem 28: Array Dependence Analysis (Difficulty: d3)

## Problem Statement

Analyze array dependencies to enable loop vectorization:

```
B1:  i = 0
     goto B2

B2:  if i < 100 goto B3 else goto B5

B3:  a[i] = b[i] + c[i]        // vectorizable?
     d[i+1] = a[i] * 2          // dependence on previous line
     e[i] = d[i+1] + f[i]       // dependence on previous line
     i = i + 1
     goto B2

B4:  // second loop
     j = 1
     goto B5

B5:  if j < 99 goto B6 else goto B7

B6:  x[j] = x[j-1] + x[j+1]    // complex dependence
     y[j] = x[j] + z[j]
     j = j + 1
     goto B5

B7:  return
```

## Tasks

1. **Define array dependence analysis** including:
   - How to represent array accesses and subscripts
   - Different types of dependencies (flow, anti, output)
   - Distance and direction vectors for dependencies

2. **Analyze the first loop (B2-B3)**:
   - Which array accesses have dependencies?
   - What are the dependency distances?
   - Which statements can be vectorized together?

3. **Analyze the second loop (B5-B6)**:
   - How does the access pattern `x[j-1], x[j], x[j+1]` affect dependencies?
   - Can this loop be vectorized?

4. **Design optimizations**:
   - Which loops can be vectorized?
   - What transformations would enable vectorization?
   - How would loop unrolling affect the dependencies?

## Expected Output Format

- Dependence analysis framework
- Dependency graphs for each loop
- Analysis of vectorization opportunities
- Proposed loop transformations