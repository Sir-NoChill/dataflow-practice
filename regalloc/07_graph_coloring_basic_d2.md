# Problem 7: Basic Graph Coloring with Limited Registers

## Problem Statement
Given the interference graph from a previous analysis, perform graph coloring register allocation assuming 3 available registers.

## Given Interference Graph
Variables: {a, b, c, d, e, f}
Edges: {(a,b), (a,c), (b,c), (b,d), (c,d), (c,e), (d,f), (e,f)}

## Task
1. Apply the graph coloring algorithm using the simplification approach
2. Show the order in which nodes are removed from the graph during simplification
3. Show the order in which nodes are colored during the selection phase
4. Assign registers R1, R2, R3 to variables
5. Identify if any spilling is required

## Expected Output Format
- Step-by-step simplification showing node removal order and remaining graph
- Step-by-step coloring showing register assignments
- Final register allocation mapping
- Analysis of whether the allocation succeeded or requires spilling