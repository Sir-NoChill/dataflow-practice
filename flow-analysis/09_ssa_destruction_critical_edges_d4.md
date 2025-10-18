# SSA Destruction and Critical Edge Splitting

## Problem Statement
Convert the following SSA form code back to conventional form, handling critical edges and parallel copy insertion.

## SSA Form Code
```
B1: x₁ = input
    if x₁ > 0 goto B3
    goto B2
B2: y₁ = x₁ * 2
    goto B4
B3: y₂ = x₁ + 5
    z₁ = y₂ * 3
    goto B4
B4: y₃ = φ(y₁, y₂)
    z₂ = φ(⊥, z₁)
    if y₃ < 10 goto B5
    goto B6
B5: x₂ = y₃ + z₂
    y₄ = x₂ - 1
    goto B4
B6: result = y₃ + z₂
    return result
```

## Tasks
1. Identify critical edges in the CFG
2. Split critical edges where necessary for correct copy insertion
3. Insert parallel copies to handle φ-function arguments
4. Convert back to conventional form with proper variable assignments
5. Ensure semantic equivalence is maintained

## Expected Output Format
- Analysis of critical edges and splitting decisions
- Modified CFG after edge splitting
- Parallel copy insertion strategy
- Final conventional form code
- Verification of semantic preservation