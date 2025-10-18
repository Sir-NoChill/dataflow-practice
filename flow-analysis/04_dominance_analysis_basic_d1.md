# Basic Dominance Analysis

## Problem Statement
Given the control flow graph represented by the following adjacency list, compute the dominance relationships.

## CFG Adjacency List
```
Entry -> B1
B1 -> B2, B3
B2 -> B4
B3 -> B4, B5
B4 -> B6
B5 -> B6
B6 -> Exit
```

## Tasks
1. Compute the dominance set Dom(n) for each node n
2. Identify the immediate dominator idom(n) for each node
3. Construct the dominance tree
4. Verify your results using the dominance definition

## Expected Output Format
- Dom(n) sets for each node
- Immediate dominator mapping
- Dominance tree representation
- Verification that d dominates n iff d appears on every path from Entry to n