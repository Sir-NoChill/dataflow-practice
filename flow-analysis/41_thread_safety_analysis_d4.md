# Thread Safety Analysis

## Problem Statement
Analyze concurrent code for thread safety issues and optimization opportunities.

## Three-Address Code
```
shared_counter = 0
shared_array[1000]
thread_local_var

function worker_thread(id):
B1: lock(mutex1)
    temp = shared_counter
    shared_counter = temp + 1
    local_id = shared_counter
    unlock(mutex1)
    goto B2

B2: for i = local_id to 1000 step num_threads
B3:   // Race condition potential
      shared_array[i] = compute(i)

      // Thread-local computation
      thread_local_var = i * id

      // Atomic operation
      atomic_add(&global_sum, shared_array[i])

      // Conditional synchronization
      if i % 100 == 0 goto B4
      goto B5
B4:   lock(mutex2)
      log_progress(i, id)
      unlock(mutex2)
B5: end for
    return
```

## Tasks
1. Identify shared variables and potential race conditions
2. Analyze lock acquisition patterns and deadlock potential
3. Determine thread-local vs shared data access patterns
4. Identify opportunities for lock elimination or coarsening
5. Analyze atomic operations and memory ordering requirements

## Expected Output Format
- Race condition analysis for shared variables
- Lock dependency graph and deadlock analysis
- Thread-local optimization opportunities
- Synchronization optimization recommendations
- Memory consistency model considerations