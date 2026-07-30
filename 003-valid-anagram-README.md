# 003. Valid Anagram

Difficulty: Easy

LeetCode: https://leetcode.com/problems/valid-anagram/

---

## Question

Given two strings `s` and `t`, return `true` if `t` is an **anagram** of `s`, and return `false` otherwise.

An anagram uses exactly the same characters with exactly the same frequencies, but the order may be different.

---

## Examples

### Example 1

**Input**

```text
s = "anagram"
t = "nagaram"
```

**Output**

```text
true
```

---

### Example 2

**Input**

```text
s = "rat"
t = "car"
```

**Output**

```text
false
```

---

## Constraints

```text
1 <= s.length, t.length <= 5 × 10⁴
`s` and `t` consist of lowercase English letters.
```

---

## Pattern

Frequency Counting

---

## Key Idea

Two strings can only be anagrams if their lengths are equal.

Count every character in `s`, then subtract the counts while reading `t`. If a character in `t` has no remaining count, return `false`. Otherwise, every character matches.

---

## Iteration Trace

**Input**

```text
s = "anagram"
t = "nagaram"
```

| Stage   | Character           | Relevant Count       | Action                               |
| ------- | ------------------- | -------------------- | ------------------------------------ |
| Count s | a                   | 3                    | Store frequency                      |
| Count s | n                   | 1                    | Store frequency                      |
| Count s | g                   | 1                    | Store frequency                      |
| Count s | r                   | 1                    | Store frequency                      |
| Count s | m                   | 1                    | Store frequency                      |
| Check t | n, a, g, a, r, a, m | Counts decrease to 0 | All characters matched → Return true |

---

## Code

```javascript
var isAnagram = function(s, t) {
    if (s.length !== t.length) {
        return false;
    }

    const count = new Map();

    for (const char of s) {
        count.set(char, (count.get(char) || 0) + 1);
    }

    for (const char of t) {
        if (!count.get(char)) {
            return false;
        }

        count.set(char, count.get(char) - 1);
    }

    return true;
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

where `k` is the number of distinct characters. For lowercase English letters, `k <= 26`, so it can also be viewed as `O(1)`.

---

## Notes

✔ Anagrams must have equal lengths.

✔ `(count.get(char) || 0) + 1` increases a character's frequency.

✔ A missing or zero count means `t` uses a character too many times.

---

## Recognition

Use this pattern when you need to:

- Compare whether two collections contain the same items
- Count character or number frequencies
- Order does not matter, but quantity does
