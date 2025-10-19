# Problem 1: Basic Reaching Definitions Analysis (Difficulty: d0)

## Problem Statement

Given the following Three Address Code (TAC), perform reaching definitions analysis.

```
B1:  x = 5
     y = x + 2
     goto B2

B2:  z = x * y
     if z > 10 goto B3 else goto B4

B3:  x = z + 1
     goto B4

B4:  y = x - 1
     return y
```

## Tasks

1. **Define the dataflow analysis framework** for reaching definitions by specifying:
   - The domain of the analysis
      - The set of all variable definitions
   - The direction of the analysis
      - Forwards
   - The generalized transfer function
      - `OUT[B] = f_B(IN[B])`
   - The boundary value
      - `OUT[START] = {}`
   - The meet operator
      - Set Union
   - The dataflow equation
      - `OUT[B] = gen[B] U (IN[B] - kill[B])`
      - `IN[B] = U_{P \in pred[P]} OUT[P]`
   - The initialization of nodes
      - `OUT[B] = {}`

2. **Apply the analysis** by hand using the iterative fixed-point algorithm until convergence.

    We first need the CFG for the program:

    ```mermaid
    graph TD
        START --> B1
        B1 --> B2
        B2 --> B3
        B2 --> B4
        B3 --> B4
        B4 --> STOP
    ```

    We start by computing the gen and kill sets for each of the basic blocks:

    | Basic Block | Gen          | Kill    |
    | ----------- | ------------ | ------- |
    | START       | `{ }`        | `{ }`   |
    | B1          | `{ x1, y1 }`   | `{ }`   |
    | B2          | `{ z }`      | `{ }`   |
    | B3          | `{ x2 }`      | `{ x1 }` |
    | B4          | `{ y2 }`      | `{ y1 }` |

    We then initialize the OUT sets for each basic block in the program and
    proceed with the iterative algorithm:

    | Iteration | Basic Block | OUT                 | IN                  |
    | --------- | ----------- | --------------------| --------------------|
    | 0         | START       | `{ }`               | `{ }`               |
    | 0         | B1          | `{ }`               | `{ }`               |
    | 0         | B2          | `{ }`               | `{ }`               |
    | 0         | B3          | `{ }`               | `{ }`               |
    | 0         | B4          | `{ }`               | `{ }`               |
    | 0         | STOP        | `{ }`               | `{ }`               |
    | 1         | START       | `{ }`               | `{ }`               |
    | 1         | B1          | `{ x1, y1 }`        | `{ }`               |
    | 1         | B2          | `{ z }`             | `{ }`               |
    | 1         | B3          | `{ x2 }`            | `{ }`               |
    | 1         | B4          | `{ y2 }`            | `{ }`               |
    | 1         | STOP        | `{ }`               | `{ }`               |
    | 2         | START       | `{ }`               | `{ }`               |
    | 2         | B1          | `{ x1, y1 }`        | `{ }`               |
    | 2         | B2          | `{ x1, y1, z }`     | `{ x1, y1 }`        |
    | 2         | B3          | `{ x2, y1, z }`     | `{ x1, y1, z }`     |
    | 2         | B4          | `{ x1, x2, y2, z }` | `{ x1, x2, y1, z }` |
    | 2         | STOP        | `{ x1, x2, y2, z }` | `{ x1, x2, y2, z }` |
    | 3         | START       | `{ }`               | `{ }`               |
    | 3         | B1          | `{ x1, y1 }`        | `{ }`               |
    | 3         | B2          | `{ x1, y1, z }`     | `{ x1, y1 }`        |
    | 3         | B3          | `{ x2, y1, z }`     | `{ x1, y1, z }`     |
    | 3         | B4          | `{ x1, x2, y2, z }` | `{ x1, x2, y1, z }` |
    | 3         | STOP        | `{ x1, x2, y2, z }` | `{ x1, x2, y2, z }` |

3. **Show your work** including:
   - The IN and OUT sets for each basic block at each iteration
   - The final converged solution

## Expected Output Format

Present your solution as IN[B] and OUT[B] sets for each basic block B1, B2, B3, B4, showing the step-by-step iterative process until no changes occur.

| Iteration | Basic Block | IN                  | OUT                 |
| 3         | START       | `{ }`               | `{ }`               |
| 3         | B1          | `{ x1, y1 }`        | `{ }`               |
| 3         | B2          | `{ x1, y1, z }`     | `{ x1, y1 }`        |
| 3         | B3          | `{ x2, y1, z }`     | `{ x1, y1, z }`     |
| 3         | B4          | `{ x2, y1, z }`     | `{ x1, x2, y1, z }` |
| 3         | STOP        | `{ x1, x2, y1, z }` | `{ x1, x2, y1, z }` |
