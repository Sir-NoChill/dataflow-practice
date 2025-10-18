# Cache Behavior Analysis

## Problem Statement
Analyze memory access patterns for cache optimization opportunities.

## Three-Address Code
```
B1: // Matrix multiplication with poor cache locality
    for i = 0 to N-1
B2:   for j = 0 to N-1
B3:     for k = 0 to N-1
B4:       // Poor cache locality: row-major × column-major
         temp = A[i][k] * B[k][j]
         C[i][j] = C[i][j] + temp
      end for
    end for
  end for

B5: // Array processing with stride issues
    for i = 0 to size step 8    // Large stride access
B6:   process(large_array[i])
    end for

B7: // Linked list traversal - poor spatial locality
    current = head
B8: if current == null goto B10
B9: process(current->data)
    current = current->next
    goto B8
B10: return
```

## Tasks
1. Analyze memory access patterns and spatial/temporal locality
2. Identify cache misses and their causes
3. Propose loop transformations for better cache performance
4. Analyze the effect of different cache configurations
5. Estimate cache miss penalties and optimization benefits

## Expected Output Format
- Memory access pattern analysis
- Cache miss prediction for different cache sizes
- Loop transformation recommendations (tiling, interchange, etc.)
- Locality optimization strategies
- Performance impact estimation