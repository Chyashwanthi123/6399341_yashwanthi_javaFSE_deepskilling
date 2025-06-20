# Recursive Algorithms & Financial Forecasting

## Q1. Understand Recursive Algorithms

### 🌀 What is Recursion?

**Recursion** is a technique where a function calls itself to solve smaller subproblems of a larger problem.

It is especially useful for problems with:
- **Overlapping subproblems**
- **Optimal substructure**

#### 📌 Key Components of a Recursive Function:
- **Base Case:** Simplest scenario where the recursion ends.
- **Recursive Case:** Function calls itself with a smaller input.

---

### 🧠 How Recursion Simplifies Problems

Recursion:
- Breaks down complex problems into smaller, manageable parts.
- Reduces the need for loops, resulting in cleaner and more elegant code.
- Is powerful in:
  - Tree and graph traversal
  - Divide and conquer algorithms (e.g., merge sort, quicksort)
  - Mathematical computations (e.g., factorial, Fibonacci, compound interest)

---

### 💡 Financial Forecasting with Recursion

Recursive functions can be used to calculate **future financial values** year-by-year.  
Each year’s value is derived from the previous year’s, making recursion a natural fit.

Example:
```java
double futureValue(double principal, double rate, int n) {
    if (n == 0) return principal;
    return futureValue(principal, rate, n - 1) * (1 + rate);
}
```

---

## Q4. Analysis

### a) Time Complexity of the Recursive Algorithm

Recursive Formula:
```
futureValue(principal, rate, n) = futureValue(principal, rate, n - 1) * (1 + rate)
Base Case: futureValue(principal, rate, 0) = principal
```

- **Time Complexity:** `O(n)` (n recursive calls)
- **Space Complexity:** `O(n)` (due to the call stack)

---

### b) Optimizing the Recursive Solution

#### ✅ 1. Convert to Iterative Approach

Avoid stack overflow and improve performance:
```java
double futureValueIterative(double principal, double rate, int n) {
    double result = principal;
    for (int i = 0; i < n; i++) {
        result *= (1 + rate);
    }
    return result;
}
```

- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(1)`

---

#### ✅ 2. Use Mathematical Formula

Use the compound interest formula:
```
Future Value = P * (1 + r)^n
```

```java
double futureValueFormula(double principal, double rate, int n) {
    return principal * Math.pow(1 + rate, n);
}
```

- **Time Complexity:** `O(1)`
- **Space Complexity:** `O(1)`

---

#### ✅ 3. Use Memoization (for complex scenarios)

Avoid repeated calculations in recursive calls:
```java
Map<Integer, Double> memo = new HashMap<>();

double futureValueMemo(double principal, double rate, int n) {
    if (n == 0) return principal;
    if (memo.containsKey(n)) return memo.get(n);
    double value = futureValueMemo(principal, rate, n - 1) * (1 + rate);
    memo.put(n, value);
    return value;
}
```

- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(n)`

---

### 📊 Summary of Optimization Methods

| Method             | Time Complexity | Space Complexity | Notes                                 |
|--------------------|-----------------|------------------|----------------------------------------|
| Recursive          | O(n)            | O(n)             | Simple but can cause stack overflow    |
| Iterative          | O(n)            | O(1)             | Safer and efficient for large inputs   |
| Math Formula       | O(1)            | O(1)             | Fastest and cleanest (for fixed rate)  |
| Recursive + Memo   | O(n)            | O(n)             | Useful for overlapping subproblems     |

---

> 🚀 Use recursion wisely for clarity and simplicity, and optimize based on problem constraints.
