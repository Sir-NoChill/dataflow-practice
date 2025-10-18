# Problem 33: Integrated Instruction Scheduling and Register Allocation

## Problem Statement
Perform register allocation while considering instruction scheduling opportunities to reduce register pressure.

## Three Address Code
```
1:  a = load array[0]
2:  b = load array[1]     // independent load
3:  c = a + 1             // depends on a
4:  d = b + 1             // depends on b
5:  e = c * 2             // depends on c
6:  f = d * 2             // depends on d
7:  g = e + f             // depends on both e and f
8:  return g
```

## Task
1. Analyze instruction dependencies and identify scheduling opportunities
2. Show how different instruction schedules affect live variable ranges
3. Apply register allocation to multiple scheduling alternatives:
   - Original order
   - Scheduled to minimize register pressure
   - Scheduled for latency optimization
4. Compare register allocation results for each schedule
5. Recommend the best integrated approach

## Expected Output Format
- Dependency analysis and scheduling opportunities
- Live variable analysis for each scheduling alternative
- Register allocation results for each schedule
- Performance trade-off analysis (register pressure vs latency)
- Recommendation for integrated scheduling/allocation