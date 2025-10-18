# Problem 26: Dataflow Analysis with Recursion (Difficulty: d5)

## Problem Statement

Apply dataflow analyses to recursive functions with careful handling of infinite call chains:

```c
int fibonacci(int n) {
    int temp1 = n - 1;
    int temp2 = n - 2;

    if (n <= 1) {
        return n;
    } else {
        int result1 = fibonacci(temp1);  // recursive call 1
        int result2 = fibonacci(temp2);  // recursive call 2
        int sum = result1 + result2;
        return sum;
    }
}

int mutual_a(int x);  // forward declaration

int mutual_b(int x) {
    if (x <= 0) {
        return 1;
    } else {
        int temp = x - 1;
        return x * mutual_a(temp);
    }
}

int mutual_a(int x) {
    if (x <= 1) {
        return x;
    } else {
        int temp = x - 2;
        return x + mutual_b(temp);
    }
}

int main() {
    int a = 5;
    int b = 10;
    int fib_result = fibonacci(a);
    int mutual_result = mutual_a(b);
    return fib_result + mutual_result;
}
```

## Tasks

1. **Model recursive call graphs**:
   - How do you represent recursive function calls in the CFG?
   - How do you handle potentially infinite call chains?

2. **Define analysis framework for recursion**:
   - Choose ONE analysis (reaching definitions, live variables, or available expressions)
   - How do you ensure termination with recursive calls?
   - How do you handle mutual recursion between `mutual_a` and `mutual_b`?

3. **Apply your chosen analysis**:
   - Show how the analysis handles the recursive structure
   - Demonstrate convergence despite recursive calls
   - Handle both direct recursion (fibonacci) and mutual recursion

4. **Optimization considerations**:
   - Which optimizations are safe in the presence of recursion?
   - How does recursion affect dead code elimination?
   - Can any recursive calls be optimized (e.g., tail call optimization)?

5. **Advanced topics**:
   - How would memoization affect your dataflow analysis?
   - What assumptions are needed about recursion depth?

## Expected Output Format

- Recursive call graph representation
- Analysis framework with termination guarantees
- Complete analysis results for your chosen dataflow problem
- Discussion of recursion-specific optimization challenges
- Consideration of advanced optimization opportunities