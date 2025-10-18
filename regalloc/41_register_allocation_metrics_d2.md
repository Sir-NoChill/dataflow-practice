# Problem 41: Register Allocation Quality Metrics

## Problem Statement
Develop and apply metrics to evaluate register allocation quality for a given allocation solution.

## Three Address Code with Two Allocation Solutions
```
1:  a = 10
2:  b = 20
3:  c = a + b
4:  d = a * 2
5:  e = b * 3
6:  f = c + d + e
7:  return f
```

## Allocation Solution A
- a → R1, b → R2, c → R3, d → R1 (reuse), e → R2 (reuse), f → R1

## Allocation Solution B
- a → R1, b → R2, c → spill, d → R3, e → spill, f → R1

## Task
1. Define register allocation quality metrics:
   - Register utilization efficiency
   - Spill operation count and cost
   - Move instruction overhead
   - Register lifetime optimization
2. Apply these metrics to both allocation solutions
3. Rank the solutions by overall quality
4. Identify situations where each metric might be most important
5. Propose a composite quality score

## Expected Output Format
- Definition and justification of each quality metric
- Quantitative analysis of both allocation solutions
- Metric-by-metric comparison
- Overall quality ranking with reasoning
- Discussion of metric trade-offs in different contexts