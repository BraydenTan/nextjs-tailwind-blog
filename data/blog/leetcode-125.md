---
title: LeetCode 125 Valid Palindrome
date: '2023-01-16'
tags: ['LeetCode']
draft: false
summary: LeetCode 125 TwoSum with JavaScript and Python
images: []
layout: PostLayout
canonicalUrl: leetcode0125
---

## LeetCode 125 Valid Palindrome

Quetions:
A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.

<b>Example 1:</b>

```md
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```

<b>Example 2:</b>

```md
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
```

<b>Example 3:</b>

```md
Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
```

<b>Constraints:</b>

```html
- 1 <= s.length <= 2 * 10<sup>5</sup> - s consists only of printable ASCII characters.
```

So the simple step

```js
const s = 'abc'
s.split('') //['a','b','c']
s.split('').reverse() //['c','b','a']
s.split('').reverse().join('') //['c','b','a']
```

this would work but will get bad complexity.

Key Idea =Think of them as words where <b>Each half mirrors each other </b>
This mirror concept works for words with both even and odd letters

- "LOL"
- "LO OL" =True
- "LO VE" =False

### Valid Palindrome PSeudocode

- Sanitize input string by removing non alphanumeric characters and lowercasing it.
- Create a left and right pointer ,initially at start and end of input string .
- While Left less than Right
  - If Characters at Left and Right Pointer are not equal ,return false
- Return True

```js
function isPalindrome(s) {
  //Sanitize the input string *include Regular Expression
  s = s.toLowerCase().replace(/[\W_]/g, '')
  //e(/W_]/g,) = grab all nun alphanumeric characters, include space ,underscore
  //LeetCode they don't test underscore but actual company will test.
  let left = 0
  let right = s.length - 1
  while (left < right) {
    if (s[left] !== s[right]) {
      return false
    }
    left++
    right--
  }
  return true
}
```

### Complexity Analysis

- Time Complexity = O(N)
- Space Complexity = O(1)
  - Left and Right Pointers take up constant space.
