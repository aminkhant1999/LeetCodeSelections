# 009. Reverse Linked List

Difficulty: Easy

LeetCode: https://leetcode.com/problems/reverse-linked-list/

---

## Question

Given the `head` of a singly linked list, reverse the list and return its new head.

---

## Examples

### Example 1

**Input**

```text
head = [1,2,3,4,5]
```

**Output**

```text
[5,4,3,2,1]
```

---

### Example 2

**Input**

```text
head = [1,2]
```

**Output**

```text
[2,1]
```

---

### Example 3

**Input**

```text
head = []
```

**Output**

```text
[]
```

---

## Constraints

```text
The number of nodes is in the range `[0, 5000]`.
-5000 <= Node.val <= 5000
```

---

## Pattern

Linked List

---

## Key Idea

Use three references:

- `previous` points to the reversed part.
- `current` points to the node being processed.
- `next` temporarily saves the rest of the original list.

Save `current.next`, reverse the pointer, then move both references forward.

---

## Iteration Trace

**Input**

```text
head = [1,2,3]
```

| Iter | Previous | Current | Saved Next | Reversed Part    |
| ---- | -------- | ------- | ---------- | ---------------- |
| 1    | null     | 1       | 2          | 1 → null         |
| 2    | 1        | 2       | 3          | 2 → 1 → null     |
| 3    | 2        | 3       | null       | 3 → 2 → 1 → null |
| End  | 3        | null    | —          | Return node 3    |

---

## Code

```javascript
var reverseList = function(head) {
    let previous = null;
    let current = head;

    while (current !== null) {
        const next = current.next;
        current.next = previous;
        previous = current;
        current = next;
    }

    return previous;
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

✔ Save `current.next` before changing it, or the remaining list will be lost.

✔ After each iteration, `previous` is the head of the reversed portion.

✔ When `current` becomes `null`, `previous` is the new head.

---

## Recognition

Use this pattern when you need to:

- Change links between nodes
- Walk through a list without array indexing
- Reverse pointer direction in place
