# Problem 20: Basic Linear Scan Register Allocation

## Problem Statement
Perform linear scan register allocation using the live intervals from the previous problem.

## Given Live Intervals (sorted by start point)
- a: [1, 5)
- b: [2, 6)
- c: [3, 6)
- d: [4, 7)
- e: [5, 7)
- f: [6, 8)

## Task
Assume 3 registers (R1, R2, R3) are available:

1. Apply the linear scan algorithm step by step
2. Show the active list and register assignments at each interval start
3. Handle any spilling decisions if register pressure exceeds capacity
4. Show the final register assignment for each variable
5. Compare register usage efficiency with graph coloring

## Expected Output Format
- Step-by-step linear scan execution showing:
  - Current interval being processed
  - Active intervals at each step
  - Register assignment decisions
  - Spill decisions (if any)
- Final register allocation mapping
- Comparison analysis with graph coloring approach