# Problem 4: Source Code to TAC Conversion and Register Analysis

## Problem Statement
Convert the following source code to Three Address Code and perform register allocation analysis.

## Source Code
```c
int compute(int a, int b) {
    int temp1 = a * b;
    int temp2 = a + b;
    if (temp1 > temp2) {
        return temp1 - temp2;
    } else {
        return temp1 + temp2;
    }
}
```

## Task
1. Convert the source code to Three Address Code
2. Perform live variable analysis on your TAC
3. Construct the interference graph
4. Estimate how many registers would be needed for this function

## Expected Output Format
- Three Address Code translation
- Live variable analysis
- Interference graph
- Register requirement analysis