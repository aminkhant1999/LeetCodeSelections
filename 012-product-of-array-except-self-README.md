# 012. Product of Array Except Self

Difficulty: Medium

LeetCode: https://leetcode.com/problems/product-of-array-except-self/

---

## Question

Given an integer array `nums`, return an array `answer` such that `answer[i]` equals the product of every element of `nums` except `nums[i]`.

The product of any prefix or suffix fits in a 32-bit integer. You must solve the problem in `O(n)` time **without using division**.

---

## Examples

### Example 1

**Input**

```text
nums = [1,2,3,4]
```

**Output**

```text
[24,12,8,6]
```

---

### Example 2

**Input**

```text
nums = [-1,1,0,-3,3]
```

**Output**

```text
[0,0,9,0,0]
```

---

## Constraints

```text
2 <= nums.length <= 10⁵
-30 <= nums[i] <= 30
The product of any prefix or suffix is guaranteed to fit in a 32-bit integer.
```

---

## Pattern

Prefix & Suffix

---

## Key Idea

For each index, the required answer is:

`product of everything on the left × product of everything on the right`

First pass: store the prefix product in `answer[i]`.

Second pass: move right to left while maintaining a suffix product, multiply it into `answer[i]`, then update the suffix.

---

## Iteration Trace

**Input**

```text
nums = [1,2,3,4]
```

| Index | Prefix Stored | Suffix Used | Final answer[i] |
| ----- | ------------- | ----------- | --------------- |
| 0     | 1             | 24          | 24              |
| 1     | 1             | 12          | 12              |
| 2     | 2             | 4           | 8               |
| 3     | 6             | 1           | 6               |

---

## Code

```javascript
var productExceptSelf = function(nums) {
    const answer = new Array(nums.length).fill(1);
    let prefix = 1;

    for (let i = 0; i < nums.length; i++) {
        answer[i] = prefix;
        prefix *= nums[i];
    }

    let suffix = 1;

    for (let i = nums.length - 1; i >= 0; i--) {
        answer[i] *= suffix;
        suffix *= nums[i];
    }

    return answer;
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

extra space, excluding the output array.

---

## Notes

✔ Do not use division.

✔ Store the product before multiplying by the current value, so the current element is excluded.

✔ The output array can hold prefix products, avoiding separate prefix and suffix arrays.

---

## Recognition

Use this pattern when you need to:

- Compute an answer using elements before and after each index
- Reuse prefix and suffix information
- Avoid repeated nested-loop calculations
