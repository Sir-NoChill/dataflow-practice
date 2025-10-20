# Problem 2: Reaching Definitions with Loops (Difficulty: d1)

## Problem Statement

Convert the following source code to Three Address Code and perform reaching definitions analysis.

```c
int x = 0;
int y = 1;
while (x < 10) {
    x = x + y;
    if (x % 2 == 0) {
        y = y * 2;
    } else {
        y = y + 1;
    }
}
return x + y;
```

## Tasks

1. **Convert to TAC**: Transform the source code into Three Address Code with appropriate basic blocks.

  ```asm
  L1: x = 0
      y = 1

  L2: if (x < 10) goto L6 else goto L3

  L3: x = x + y
      if (x % 2 == 0) goto L4 else goto L5

  L4: y = y * 2
      goto L2

  L5: y = y + 1
      goto L2

  L6: return x + y
  ```

2. **Define the dataflow framework** for reaching definitions analysis.
  - Domain: All definitions in the program
  - Direction: Forward
  - Transfer Function: `OUT[B] = f_B(IN[B])`
  - Boundary: `OUT[START] = { }`
  - Meet Operator: Set Union
  - Initialization: `OUT[B] = { }`
  - Equations:
    - `OUT[B] = gen[B] U (IN[B] - kill[B])`
    - `IN[B] = U_{P \in pred(B)} OUT[P]`

3. **Construct the CFG**: Draw or describe the control flow graph showing all basic blocks and edges.

  ```mermaid
  graph TD
    START --> B1
    B1 --> B2
    B2 --> B3
    B2 --> B6
    B3 --> B4
    B3 --> B5
    B4 --> B2
    B5 --> B2
    B6 --> STOP
  ```

4. **Apply reaching definitions analysis** using the iterative algorithm, paying special attention to how the loop affects convergence.

First we define the gen and kill sets of each basic block:
| Basic Block | Gen          | Kill         |
| ----------- | ------------ | ------------ |
| START       | `{ }`        | `{ }`        |
| B1          | `{ x1, y1 }` | `{ }`        |
| B2          | `{ }`        | `{ }`        |
| B3          | `{ x2 }`     | `{ x* }`     |
| B4          | `{ y2 }`     | `{ y* }`     |
| B5          | `{ y3 }`     | `{ y* }`     |
| B6          | `{ }`        | `{ }`        |
| STOP        | `{ }`        | `{ }`        |

| Iteration | Basic Block | IN                       | OUT                      |
| --------- | ----------- | ------------------------ | ------------------------ |
| 0         | START       | `{ }`                    | `{ }`                    |
| 0         | B1          | `{ }`                    | `{ }`                    |
| 0         | B2          | `{ }`                    | `{ }`                    |
| 0         | B3          | `{ }`                    | `{ }`                    |
| 0         | B4          | `{ }`                    | `{ }`                    |
| 0         | B5          | `{ }`                    | `{ }`                    |
| 0         | B6          | `{ }`                    | `{ }`                    |
| 0         | STOP        | `{ }`                    | `{ }`                    |
| 1         | START       | `{ }`                    | `{ }`                    |
| 1         | B1          | `{ }`                    | `{ x1, y1 }`             |
| 1         | B2          | `{ x1, y1 }`             | `{ x1, y1 }`             |
| 1         | B3          | `{ x1, y1 }`             | `{ x2, y1 }`             |
| 1         | B4          | `{ x2, y1 }`             | `{ x2, y2 }`             |
| 1         | B5          | `{ x2, y1 }`             | `{ x2, y3 }`             |
| 1         | B6          | `{ x1, y1 }`             | `{ x1, y1 }`             |
| 1         | STOP        | `{ x1, y1 }`             | `{ x1, y1 }`             |
| 2         | START       | `{ }`                    | `{ }`                    |
| 2         | B1          | `{ }`                    | `{ x1, y1 }`             |
| 2         | B2          | `{ x1, x2, y1, y2, y3 }` | `{ x1, x2, y1, y2, y3 }` |
| 2         | B3          | `{ x1, y1, y2, y3, x2 }` | `{ x2, y1, y2, y3 }`     |
| 2         | B4          | `{ x2, y1, y2, y3 }`     | `{ x2, y2 }`             |
| 2         | B5          | `{ x2, y1, y2, y3 }`     | `{ x2, y3 }`             |
| 2         | B6          | `{ x1, x2, y1, y2, y3 }` | `{ x1, x2, y1, y2, y3 }` |
| 2         | STOP        | `{ x1, x2, y1, y2, y3 }` | `{ x1, x2, y1, y2, y3 }` |
| 3         | START       | `{ }`                    | `{ }`                    |
| 3         | B1          | `{ }`                    | `{ x1, y1 }`             |
| 3         | B2          | `{ x1, x2, y1, y2, y3 }` | `{ x1, x2, y1, y2, y3 }` |
| 3         | B3          | `{ x1, x2, y1, y2, y3 }` | `{ x2, y1, y2, y3 }`     |
| 3         | B4          | `{ x2, y1, y2, y3 }`     | `{ x2, y2 }`             |
| 3         | B5          | `{ x2, y1, y2, y3 }`     | `{ x2, y3 }`             |
| 3         | B6          | `{ x1, x2, y1, y2, y3 }` | `{ x1, x2, y1, y2, y3 }` |
| 3         | STOP        | `{ x1, x2, y1, y2, y3 }` | `{ x1, x2, y1, y2, y3 }` |

5. **Identify interesting cases**: Note any definitions that reach multiple points or are killed and redefined.
    - There are a couple interesting cases in this example:
        1. `x1` reaches the end of the program as well as `x2`
        2. `y` is killed and redefined multiple times, leading to all possible
           values of y reaching the end of the program
        3. The inner values of `y` and `x` are subsets of the definitions in the
           whole program due to `x` and `y` being killed within control flow

## Expected Output Format

- TAC representation with labeled basic blocks
- CFG description
- Complete IN/OUT sets for each iteration until convergence
- Brief analysis of which definitions reach the return statement
