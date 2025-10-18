# Call Graph Construction

## Problem Statement
Build a call graph for the following program with direct calls, function pointers, and virtual dispatch.

## Three-Address Code
```
// Function main
main:
    fptr = &processData
    call init()
    call fptr(data)
    obj = new Object()
    vtable = obj->vtable
    method = vtable[2]
    call method(obj, args)
    return

// Function init
init:
    if debug goto L1
    call setupNormal()
    return
L1: call setupDebug()
    return

// Function processData
processData:
    call helper1(param1)
    if condition goto L2
    call helper2(param2)
    return
L2: call helper3(param3)
    return

// Function helper1
helper1:
    call utility()
    return

// Function helper2
helper2:
    call utility()
    call external_lib_func()
    return

// Function helper3
helper3:
    fptr2 = select_function(type)
    call fptr2(data)
    return
```

## Tasks
1. Construct the static call graph with direct function calls
2. Handle function pointer calls with points-to analysis
3. Model virtual method dispatch with class hierarchy information
4. Identify strongly connected components for recursion analysis
5. Compute call graph metrics (depth, fan-in, fan-out)

## Expected Output Format
- Static call graph with direct call edges
- Enhanced call graph including indirect calls
- Analysis of function pointer targets and virtual method resolution
- SCC identification and recursion analysis
- Call graph statistics and complexity metrics