# 001. Two Sum

Difficulty: Easy

---

## Question

Given an array of integers `nums` and an integer `target`,
return the indices of the two numbers such that they add up to `target`.

You may assume that each input has **exactly one solution**, and you may **not use the same element twice**.

Return the answer in any order.

---

## Examples

### Example 1

**Input**

```text
nums = [2,7,11,15]
target = 9
```

**Output**

```text
[0,1]
```

---

### Example 2

**Input**

```text
nums = [3,2,4]
target = 6
```

**Output**

```text
[1,2]
```

---

### Example 3

**Input**

```text
nums = [3,3]
target = 6
```

**Output**

```text
[0,1]
```

---

## Constraints

```text
2 <= nums.length <= 10⁴
-10⁹ <= nums[i] <= 10⁹
-10⁹ <= target <= 10⁹
Exactly one valid answer exists.
```

---

## Pattern

Hash Map

---

## Key Idea

Instead of searching every pair,
store previously visited numbers.

For every number:

Need = target - current number

If the needed number already exists inside the HashMap,
return both indices.

Otherwise,
store current number.

---

## Iteration Trace

Input

```text
nums = [2,7,11,15]
target = 9
```

| Iter | i | Current | Need | Map Before | Action | Map After |
|------|---|---------|------|------------|--------|-----------|
|1|0|2|7|{}|Store 2 → 0|{2 → 0}|
|2|1|7|2|{2 → 0}|Found → Return [0,1]|End|

---

## Code

```javascript
var twoSum = (nums, target) => {
    const map = new Map();

    for (let i = 0; i < nums.length; i++) {
        const num = nums[i];
        const complement = target - num;

        if (map.has(complement)) {
            return [map.get(complement), i];
        }

        map.set(num, i);
    }
};
```

---

## Complexity

**Time**

```
O(n)
```

**Space**

```
O(n)
```

---

## Notes

✔ HashMap stores:

```
number → index
```

✔ Complement

```
target - current
```

✔ Check first

```
map.has(complement)
```

✔ Store later

```
map.set(num, i)
```

Otherwise the same element could be used twice.

✔ HashMap lookup

```
O(1) average
```

---

## Recognition

Use this pattern when you need to:

- Find a complement
- Check if you've seen a value before
- Perform fast lookups while scanning an array
