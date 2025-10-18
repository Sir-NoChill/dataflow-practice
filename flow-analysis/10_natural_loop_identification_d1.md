# Natural Loop Identification

## Problem Statement
Given the following control flow graph, identify all natural loops and their properties.

## Three-Address Code
```
B1: i = 0
    goto B2
B2: if i >= n goto B8
B3: j = 0
    goto B4
B4: if j >= m goto B7
B5: temp = arr[i][j]
    if temp > max goto B6
    goto B6
B6: j = j + 1
    goto B4
B7: i = i + 1
    goto B2
B8: return max
```

## Tasks
1. Construct the control flow graph
2. Identify all back edges using dominance relationships
3. Find all natural loops by determining loop bodies
4. Identify loop headers and preheaders
5. Determine loop nesting relationships

## Expected Output Format
- CFG with back edges clearly marked
- List of all natural loops with their constituent basic blocks
- Loop header identification for each loop
- Loop nesting forest representation
- Analysis of whether any loops share headers