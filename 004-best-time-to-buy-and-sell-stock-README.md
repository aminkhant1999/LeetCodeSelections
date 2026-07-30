# 004. Best Time to Buy and Sell Stock

Difficulty: Easy

LeetCode: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

---

## Question

You are given an array `prices` where `prices[i]` is the price of a stock on day `i`.

Choose one day to buy and a **later** day to sell. Return the maximum profit you can achieve. If no profit is possible, return `0`.

---

## Examples

### Example 1

**Input**

```text
prices = [7,1,5,3,6,4]
```

**Output**

```text
5
```

**Explanation**

Buy at `1` and sell later at `6`.

---

### Example 2

**Input**

```text
prices = [7,6,4,3,1]
```

**Output**

```text
0
```

**Explanation**

The price always falls, so no profitable trade exists.

---

## Constraints

```text
1 <= prices.length <= 10⁵
0 <= prices[i] <= 10⁴
```

---

## Pattern

Greedy

---

## Key Idea

Scan the prices once while tracking:

- The lowest price seen so far—the best buying price.
- The largest profit seen so far.

At each price, calculate `price - minPrice`, then update the maximum profit.

---

## Iteration Trace

**Input**

```text
prices = [7,1,5,3,6,4]
```

| Day | Price | Minimum So Far | Profit If Sold Today | Maximum Profit |
| --- | ----- | -------------- | -------------------- | -------------- |
| 0   | 7     | 7              | 0                    | 0              |
| 1   | 1     | 1              | 0                    | 0              |
| 2   | 5     | 1              | 4                    | 4              |
| 3   | 3     | 1              | 2                    | 4              |
| 4   | 6     | 1              | 5                    | 5              |
| 5   | 4     | 1              | 3                    | 5              |

---

## Code

```javascript
var maxProfit = function(prices) {
    let minPrice = Infinity;
    let maxProfit = 0;

    for (const price of prices) {
        minPrice = Math.min(minPrice, price);
        maxProfit = Math.max(maxProfit, price - minPrice);
    }

    return maxProfit;
};
```

---

## Complexity

**Time**

```text
O(n)
```

**Space**

```text
O(1)
```

---

## Notes

✔ The buying day always comes before or on the current selling day.

✔ `minPrice` represents the best purchase opportunity so far.

✔ Starting `maxProfit` at `0` handles falling prices.

---

## Recognition

Use this pattern when you need to:

- Find the best difference while preserving order
- Track a minimum or maximum seen so far
- Make the best local choice during one scan
