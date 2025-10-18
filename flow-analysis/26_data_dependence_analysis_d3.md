# Data Dependence Analysis

## Problem Statement
Analyze data dependencies for parallelization and instruction scheduling opportunities.

## Three-Address Code
```
B1: for i = 0 to n-1
B2:   a[i] = b[i] + c[i]           // S1
      d[i] = a[i] * 2              // S2
      e[i+1] = d[i] + e[i]         // S3
      f[i] = g[i-1] + h[i]         // S4
      if i > 0 goto B3
      goto B4
B3:   j[i] = a[i-1] + b[i+1]      // S5
      goto B4
B4:   k[i] = f[i] + j[i]          // S6
B5: end for
```

## Tasks
1. Identify true (flow), anti (WAR), and output (WAW) dependencies
2. Analyze loop-carried vs loop-independent dependencies
3. Determine dependency distances and directions
4. Find parallelizable statements and vectorization opportunities
5. Propose instruction scheduling within dependency constraints

## Expected Output Format
- Dependency matrix showing all statement pairs
- Classification of dependency types (flow, anti, output)
- Loop-carried dependency analysis with distances
- Parallelization opportunities identification
- Instruction scheduling recommendations