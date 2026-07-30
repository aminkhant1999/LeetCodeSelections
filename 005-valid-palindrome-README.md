# 005. Valid Palindrome

Difficulty: Easy

LeetCode: https://leetcode.com/problems/valid-palindrome/

---

## Question

A phrase is a palindrome if, after converting uppercase letters to lowercase and removing all non-alphanumeric characters, it reads the same forward and backward.

Given a string `s`, return `true` if it is a palindrome, or `false` otherwise.

---

## Examples

### Example 1

**Input**

```text
s = "A man, a plan, a canal: Panama"
```

**Output**

```text
true
```

**Explanation**

After cleaning: `amanaplanacanalpanama`.

---

### Example 2

**Input**

```text
s = "race a car"
```

**Output**

```text
false
```

**Explanation**

After cleaning: `raceacar`.

---

### Example 3

**Input**

```text
s = " "
```

**Output**

```text
true
```

**Explanation**

After removing non-alphanumeric characters, the string is empty.

---

## Constraints

```text
1 <= s.length <= 2 × 10⁵
`s` consists only of printable ASCII characters.
```

---

## Pattern

Two Pointers

---

## Key Idea

Place one pointer at each end of the string.

1. Move the left pointer past non-alphanumeric characters.
2. Move the right pointer past non-alphanumeric characters.
3. Compare the lowercase characters.
4. If they differ, return `false`; otherwise move inward.

---

## Iteration Trace

**Input**

```text
s = "A man, a plan, a canal: Panama"
```

| Step | Left Character | Right Character | Action                        |
| ---- | -------------- | --------------- | ----------------------------- |
| 1    | A              | a               | Match (case-insensitive)      |
| 2    | m              | m               | Match                         |
| 3    | a              | a               | Match                         |
| 4    | n              | n               | Match                         |
| …    | …              | …               | All pairs match → Return true |

---

## Code

```javascript
var isPalindrome = function(s) {
    let left = 0;
    let right = s.length - 1;
    const isAlphaNumeric = (char) => /[a-z0-9]/i.test(char);

    while (left < right) {
        while (left < right && !isAlphaNumeric(s[left])) {
            left++;
        }

        while (left < right && !isAlphaNumeric(s[right])) {
            right--;
        }

        if (s[left].toLowerCase() !== s[right].toLowerCase()) {
            return false;
        }

        left++;
        right--;
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
O(1)
```

---

## Notes

✔ Two pointers avoid building a separate cleaned string.

✔ Ignore punctuation and spaces.

✔ Compare characters without case sensitivity.

---

## Recognition

Use this pattern when you need to:

- Compare values from both ends
- Check symmetry
- Process pairs that move toward the centre
