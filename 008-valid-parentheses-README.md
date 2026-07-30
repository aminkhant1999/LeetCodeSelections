# 008. Valid Parentheses

Difficulty: Easy

LeetCode: https://leetcode.com/problems/valid-parentheses/

---

## Question

Given a string `s` containing only `(`, `)`, `{`, `}`, `[` and `]`, determine whether the input string is valid.

A string is valid when every opening bracket is closed by the same type of bracket and in the correct order.

---

## Examples

### Example 1

**Input**

```text
s = "()"
```

**Output**

```text
true
```

---

### Example 2

**Input**

```text
s = "()[]{}"
```

**Output**

```text
true
```

---

### Example 3

**Input**

```text
s = "(]"
```

**Output**

```text
false
```

---

### Example 4

**Input**

```text
s = "([])"
```

**Output**

```text
true
```

---

## Constraints

```text
1 <= s.length <= 10⁴
`s` consists only of parentheses and brackets: `()[]{}`.
```

---

## Pattern

Stack

---

## Key Idea

Use a stack to remember opening brackets.

- Push every opening bracket.
- For a closing bracket, the top of the stack must contain its matching opener.
- At the end, the stack must be empty.

---

## Iteration Trace

**Input**

```text
s = "([])"
```

| Iter | Character | Stack Before | Action          | Stack After      |
| ---- | --------- | ------------ | --------------- | ---------------- |
| 1    | (         | []           | Push            | [(]              |
| 2    | [         | [(]          | Push            | [(, []           |
| 3    | ]         | [(, []       | Matches [ → Pop | [(]              |
| 4    | )         | [(]          | Matches ( → Pop | [] → Return true |

---

## Code

```javascript
var isValid = function(s) {
    const stack = [];
    const pairs = {
        ")": "(",
        "]": "[",
        "}": "{"
    };

    for (const char of s) {
        if (char === "(" || char === "[" || char === "{") {
            stack.push(char);
        } else if (stack.pop() !== pairs[char]) {
            return false;
        }
    }

    return stack.length === 0;
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

✔ A stack follows Last In, First Out (LIFO).

✔ The most recent opening bracket must close first.

✔ A non-empty stack at the end means some brackets were never closed.

---

## Recognition

Use this pattern when you need to:

- Match nested pairs
- Process the most recently opened item first
- Validate opening and closing symbols
