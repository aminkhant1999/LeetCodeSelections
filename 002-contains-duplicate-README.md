# 002. Contains Duplicate

Difficulty: Easy

LeetCode: https://leetcode.com/problems/contains-duplicate/

---

## Question

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

---

## Examples

### Example 1

**Input**

```text
nums = [1,2,3,1]
```

**Output**

```text
true
```

**Explanation**

The number `1` appears twice.

---

### Example 2

**Input**

```text
nums = [1,2,3,4]
```

**Output**

```text
false
```

**Explanation**

Every value is unique.

---

### Example 3

**Input**

```text
nums = [1,1,1,3,3,4,3,2,4,2]
```

**Output**

```text
true
```

**Explanation**

Several values appear more than once.

---

## Constraints

```text
1 <= nums.length <= 10⁵
-10⁹ <= nums[i] <= 10⁹
```

---

## Pattern

Hash Set

---

## Key Idea

Use a `Set` to remember every number already visited.

For each number:

1. If it is already in the set, a duplicate exists—return `true`.
2. Otherwise, add it to the set.
3. If the loop finishes, return `false`.

---

## Iteration Trace

**Input**

```text
nums = [1,2,3,1]
```

| Iter | Current | Set Before | Action                        | Set After |
| ---- | ------- | ---------- | ----------------------------- | --------- |
| 1    | 1       | {}         | Add 1                         | {1}       |
| 2    | 2       | {1}        | Add 2                         | {1,2}     |
| 3    | 3       | {1,2}      | Add 3                         | {1,2,3}   |
| 4    | 1       | {1,2,3}    | Found duplicate → Return true | End       |

---

## Code

```javascript
var containsDuplicate = function(nums) {
    const seen = new Set();

    for (const num of nums) {
        if (seen.has(num)) {
            return true;
        }

        seen.add(num);
    }

    return false;
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
O(n)
```

---

## Notes

✔ A `Set` stores unique values only.

✔ `seen.has(num)` is `O(1)` on average.

✔ Check before adding so you can detect whether the value appeared earlier.

---

## Recognition

Use this pattern when you need to:

- Detect duplicates
- Check whether a value has appeared before
- Track unique values while scanning
