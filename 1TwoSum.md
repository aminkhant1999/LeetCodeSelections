# 001. Two Sum

Difficulty: Easy

---

## Question

Given an array of integers `nums` and an integer `target`,
return the indices of the two numbers such that they add up to `target`.

Example

Input:

nums = [2,7,11,15]

target = 9

Output:

[0,1]

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

nums = [2,7,11,15]

target = 9

| Iter | i | Current | Need | Map Before | Action | Map After |
|------|---|---------|------|------------|--------|-----------|
|1|0|2|7|{}|Store 2→0|{2→0}|
|2|1|7|2|{2→0}|Found → Return [0,1]|End|

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
}
```

---

## Complexity

Time

O(n)

Space

O(n)

---

## Notes

✔ HashMap stores:

number → index

✔ Complement

target - current

✔ Check first

✔ Store later

Otherwise the same element could be used twice.