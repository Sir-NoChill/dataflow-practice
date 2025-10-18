# Problem 25: Interprocedural Live Variables with Escape Analysis (Difficulty: d5)

## Problem Statement

Perform interprocedural live variable analysis combined with escape analysis on the following program with pointers and heap allocation:

```c
struct Point { int x, y; };

struct Point* create_point(int a, int b) {
    struct Point* p = malloc(sizeof(struct Point));
    p->x = a;
    p->y = b;
    int temp = a + b;  // local variable
    return p;  // p escapes, temp doesn't
}

void modify_point(struct Point* pt, int dx, int dy) {
    pt->x = pt->x + dx;
    pt->y = pt->y + dy;
    int local = dx * dy;  // doesn't escape
    // local is dead at function exit
}

int main() {
    int val1 = 10;
    int val2 = 20;
    struct Point* point = create_point(val1, val2);

    modify_point(point, 5, 3);

    int result = point->x + point->y;
    free(point);

    int unused = val1 + val2;  // potentially dead
    return result;
}
```

## Tasks

1. **Convert to TAC** with explicit pointer operations and heap allocations.

2. **Define interprocedural live variable framework** accounting for:
   - Variables that escape through return values
   - Variables that escape through pointer parameters
   - Heap-allocated memory liveness

3. **Perform escape analysis**:
   - Which variables escape their function scope?
   - Which variables are only used locally?
   - How does escape analysis affect liveness?

4. **Apply interprocedural live analysis**:
   - Which local variables are dead at function exit?
   - How do escaped variables affect caller liveness?
   - Which heap allocations remain live across function boundaries?

5. **Advanced optimizations**:
   - Which local variables can be eliminated?
   - Can any heap allocations be stack-allocated instead?
   - Which pointer updates are necessary for correctness?

## Expected Output Format

- TAC with explicit pointer and heap operations
- Escape analysis results
- Interprocedural live variable analysis
- Optimization opportunities with safety analysis
- Discussion of heap vs. stack allocation decisions