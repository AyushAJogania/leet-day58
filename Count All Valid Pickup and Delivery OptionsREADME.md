# leet-day58

# Counting Valid Pickup and Delivery Orders - Readme

## Problem Description

You are given `n` orders, each consisting of pickup and delivery services. Your task is to count all valid pickup/delivery sequences such that delivery `i` always occurs after pickup `i`.

Since the answer may be large, you need to return it modulo 10^9 + 7.

## Example

**Input:**
```
n = 2
```

**Output:**
```
6
```

**Explanation:**
All possible valid orders are:
1. (P1, P2, D1, D2)
2. (P1, P2, D2, D1)
3. (P1, D1, P2, D2)
4. (P2, P1, D1, D2)
5. (P2, P1, D2, D1)
6. (P2, D2, P1, D1)

## Constraints

- `1 <= n <= 500`

## Approach

The solution uses a recursive approach with memoization. It calculates the number of valid orders for `n` pairs by breaking down the problem into smaller subproblems. The key insight is that for each additional pair, there are `(2 * remainingPairs - 1) * remainingPairs` valid orders.

Here's a step-by-step explanation of the code:

1. Define a constant `MOD` for modulus in calculations and declare a vector `memoization` to store computed values.

2. Implement the `calculateOrdersCount` function. It's a recursive function that takes the number of remaining pairs as an argument.

   - Base case: If there are no remaining pairs (`remainingPairs == 0`), return 1 because there's only one valid order (no pickup or delivery).
   
   - Check if the value is already computed in the `memoization` array. If so, return it to avoid redundant calculations.
   
   - Calculate the number of valid orders for the remaining pairs using the formula `(2 * remainingPairs - 1) * remainingPairs % MOD`. This formula represents the number of ways to insert the new pair into the existing valid orders.
   
   - Store the result in the `memoization` array for future reference and return it.

3. Implement the `countOrders` function. It initializes the `memoization` array with -1 values and calls `calculateOrdersCount` with the given `numPairs`.

4. Return the count of valid orders modulo 10^9 + 7 as specified in the problem statement.

## Usage

You can use this code to count the number of valid pickup and delivery orders for a given number of pairs (`numPairs`). Simply call the `countOrders` function with the desired `numPairs`, and it will return the count of valid orders.

```cpp
Solution solution;
int numPairs = 2;
int result = solution.countOrders(numPairs);
cout << "Count of valid orders: " << result << endl;
```

## Complexity Analysis

- Time Complexity: O(n) - The recursive approach computes valid orders for each pair once and stores the results in the `memoization` array, reducing redundant calculations.

- Space Complexity: O(n) - The `memoization` array stores the results for each subproblem, consuming linear space in terms of `n`.

