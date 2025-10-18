# Field-Sensitive Alias Analysis

## Problem Statement
Perform field-sensitive alias analysis on the following code with structure field accesses.

## Three-Address Code
```
struct Point { int x, y; };
struct Rectangle { Point tl, br; };

B1: rect = malloc(sizeof(Rectangle))
    p1 = &rect->tl
    p2 = &rect->br
    px = &rect->tl.x
    py = &rect->tl.y
    goto B2
B2: if condition goto B3
    goto B4
B3: *px = 10
    *py = 20
    temp = &rect->br.x
    *temp = 30
    goto B5
B4: p1->x = 15
    p1->y = 25
    p2->x = 35
    p2->y = 45
    goto B5
B5: result_x = rect->tl.x
    result_y = rect->br.y
    return result_x + result_y
```

## Tasks
1. Model struct fields as separate abstract locations
2. Track field-specific points-to relationships
3. Analyze how field assignments affect different structure components
4. Determine which field accesses might alias
5. Compare precision with field-insensitive analysis

## Expected Output Format
- Field-sensitive abstract location model
- Points-to relationships for each field access
- Field modification analysis through different paths
- Alias pairs for field accesses
- Precision comparison: field-sensitive vs field-insensitive results