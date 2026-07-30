# 007. Binary Search

Difficulty: Easy

LeetCode: https://leetcode.com/problems/binary-search/

---

## Question

Given a **sorted** array of integers `nums` and an integer `target`, return the index of `target` if it exists. Otherwise, return `-1`.

Your algorithm must run in `O(log n)` time.

---

## Examples

### Example 1

**Input**

```text
nums = [-1,0,3,5,9,12]
target = 9
```

**Output**

```text
4
```

---

### Example 2

**Input**

```text
nums = [-1,0,3,5,9,12]
target = 2
```

**Output**

```text
-1
```

---

## Constraints

```text
1 <= nums.length <= 10⁴
-10⁴ < nums[i], target < 10⁴
All integers in `nums` are unique.
`nums` is sorted in ascending order.
```

---

## Pattern

Binary Search

---

## Key Idea

Because the array is sorted, compare the target with the middle value.

- If equal, return the middle index.
- If the target is smaller, discard the right half.
- If the target is larger, discard the left half.

Repeat until the search range is empty.

---

## Iteration Trace

**Input**

```text
nums = [-1,0,3,5,9,12]
target = 9
```

| Iter | Left | Right | Middle | nums[Middle] | Action                      |
| ---- | ---- | ----- | ------ | ------------ | --------------------------- |
| 1    | 0    | 5     | 2      | 3            | Target is larger → left = 3 |
| 2    | 3    | 5     | 4      | 9            | Found → Return 4            |

---

## Code

```javascript
var search = function(nums, target) {
    let left = 0;
    let right = nums.length - 1;

    while (left <= right) {
        const middle = Math.floor((left + right) / 2);

        if (nums[middle] === target) {
            return middle;
        }

        if (nums[middle] < target) {
            left = middle + 1;
        } else {
            right = middle - 1;
        }
    }

    return -1;
};
```

---

## Complexity

**Time**

```text
O(log n)
```

**Space**

```text
O(1)
```

---

## Notes

✔ Binary search requires sorted data.

✔ Use `left <= right` because a one-element range must still be checked.

✔ Always exclude `middle` when updating a boundary, or the loop may never end.

---

## Recognition

Use this pattern when you need to:

- Search sorted data
- Repeatedly eliminate half of the possibilities
- Meet an explicit `O(log n)` requirement
