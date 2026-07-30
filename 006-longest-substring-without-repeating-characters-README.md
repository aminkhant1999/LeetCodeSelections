# 006. Longest Substring Without Repeating Characters

Difficulty: Medium

LeetCode: https://leetcode.com/problems/longest-substring-without-repeating-characters/

---

## Question

Given a string `s`, find the length of the longest **substring** without repeating characters.

A substring is a contiguous sequence of characters.

---

## Examples

### Example 1

**Input**

```text
s = "abcabcbb"
```

**Output**

```text
3
```

**Explanation**

The answer is `abc`, with length `3`.

---

### Example 2

**Input**

```text
s = "bbbbb"
```

**Output**

```text
1
```

**Explanation**

The answer is `b`, with length `1`.

---

### Example 3

**Input**

```text
s = "pwwkew"
```

**Output**

```text
3
```

**Explanation**

The answer is `wke`, with length `3`. `pwke` is not a substring because it is not contiguous.

---

## Constraints

```text
0 <= s.length <= 5 × 10⁴
`s` consists of English letters, digits, symbols, and spaces.
```

---

## Pattern

Sliding Window

---

## Key Idea

Maintain a window from `left` to `right` containing only unique characters.

Expand `right` one character at a time. If the new character already exists in the window, remove characters from the left until it becomes unique again. Track the largest window length.

---

## Iteration Trace

**Input**

```text
s = "abcabcbb"
```

| Right | Character | Window Before | Action                      | Window After | Max |
| ----- | --------- | ------------- | --------------------------- | ------------ | --- |
| 0     | a         | ""            | Add a                       | "a"          | 1   |
| 1     | b         | "a"           | Add b                       | "ab"         | 2   |
| 2     | c         | "ab"          | Add c                       | "abc"        | 3   |
| 3     | a         | "abc"         | Remove through old a; add a | "bca"        | 3   |
| 4     | b         | "bca"         | Remove through old b; add b | "cab"        | 3   |
| 5     | c         | "cab"         | Remove through old c; add c | "abc"        | 3   |

---

## Code

```javascript
var lengthOfLongestSubstring = function(s) {
    const window = new Set();
    let left = 0;
    let maxLength = 0;

    for (let right = 0; right < s.length; right++) {
        while (window.has(s[right])) {
            window.delete(s[left]);
            left++;
        }

        window.add(s[right]);
        maxLength = Math.max(maxLength, right - left + 1);
    }

    return maxLength;
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
O(k)
```

where `k` is the number of unique characters inside the window.

---

## Notes

✔ A substring must be contiguous.

✔ `right - left + 1` is the current window length.

✔ Each character enters and leaves the set at most once.

---

## Recognition

Use this pattern when you need to:

- Find a longest or shortest contiguous range
- Maintain a condition while expanding a window
- Shrink from the left when the condition becomes invalid
