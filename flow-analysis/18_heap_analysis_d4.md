# Heap Analysis with Dynamic Allocation

## Problem Statement
Analyze heap-allocated objects and their aliasing relationships in the following code.

## Three-Address Code
```
B1: obj1 = malloc(sizeof(Node))
    obj2 = malloc(sizeof(Node))
    obj1->data = 100
    obj1->next = obj2
    obj2->data = 200
    obj2->next = null
    head = obj1
    goto B2
B2: current = head
    count = 0
    goto B3
B3: if current == null goto B7
B4: if current->data > 150 goto B5
    goto B6
B5: new_node = malloc(sizeof(Node))
    new_node->data = current->data * 2
    new_node->next = current->next
    current->next = new_node
    goto B6
B6: current = current->next
    count = count + 1
    if count > 10 goto B7
    goto B3
B7: return head
```

## Tasks
1. Model heap objects with allocation site abstraction
2. Track pointer chains through dynamically allocated structures
3. Analyze how heap modifications affect reachability
4. Handle potential memory leaks and dangling pointers
5. Determine shape properties of heap data structures

## Expected Output Format
- Allocation site abstraction model
- Heap shape evolution through program execution
- Reachability analysis from root pointers
- Memory safety analysis (leaks, dangling pointers)
- Abstract heap graph at key program points