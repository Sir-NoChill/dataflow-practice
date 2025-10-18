# Post-dominance and Control Dependence Analysis

## Problem Statement
Given the following control flow graph with multiple exit points, compute post-dominance relationships and control dependence.

## Three-Address Code
```
Entry:
    goto B1
B1: input = read()
    if input < 0 goto Exit1
B2: if input == 0 goto B4
B3: result = compute(input)
    if result > 100 goto Exit2
    goto B5
B4: result = 0
    goto B5
B5: output(result)
    if debug goto B6
    goto Exit3
B6: log(result)
    goto Exit3
Exit1: error("negative input")
       return -1
Exit2: error("overflow")
       return -2
Exit3: return 0
```

## Tasks
1. Construct the CFG including all exit nodes
2. Compute post-dominance sets for each node
3. Build the post-dominance tree
4. Calculate control dependence relationships
5. Identify nodes that control the execution of other nodes

## Expected Output Format
- CFG with multiple exits
- Post-dominance sets PostDom(n)
- Post-dominance tree
- Control dependence pairs (controlling node, dependent node)
- Analysis of which conditions control which code regions