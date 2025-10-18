# Problem 29: Vector Register Allocation

## Problem Statement
Perform register allocation for vector operations with specialized vector register constraints.

## Three Address Code
```
1:  vec_a = load_vector(array1)     // 128-bit vector
2:  vec_b = load_vector(array2)     // 128-bit vector
3:  scalar_x = 42                   // 32-bit scalar
4:  vec_c = vec_a + vec_b          // vector addition
5:  vec_d = broadcast(scalar_x)     // scalar to vector
6:  vec_e = vec_c * vec_d          // vector multiplication
7:  scalar_y = extract(vec_e, 0)    // vector to scalar
8:  vec_f = shuffle(vec_a, vec_b)   // vector permutation
9:  store_vector(vec_f, array3)
10: return scalar_y
```

## Architecture Constraints
- 4 vector registers: V1, V2, V3, V4 (128-bit each)
- 4 scalar registers: R1, R2, R3, R4 (32-bit each)
- Some operations can use either register type with conversion cost

## Task
1. Classify operations by register type requirements
2. Handle mixed scalar/vector register allocation
3. Consider conversion costs when choosing register types
4. Apply register allocation for both register classes
5. Optimize for minimal conversion overhead

## Expected Output Format
- Operation classification by register type
- Separate allocation for scalar and vector registers
- Conversion cost analysis and optimization
- Final allocation with conversion minimization
- Performance analysis of register type choices