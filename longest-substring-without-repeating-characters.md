# Longest Substring Without Repeating Characters

To solve the "Longest Substring Without Repeating Characters" problem in JavaScript, you can use the sliding window technique along with a hash map to keep track of the characters and their indices in the substring. Here's a JavaScript solution:

```javascript
function lengthOfLongestSubstring(s) {
  let maxLength = 0;
  let start = 0;
  const charIndexMap = {};

  for (let end = 0; end < s.length; end++) {
    const char = s[end];
    if (charIndexMap[char] !== undefined) {
      // If the character is already in the substring, update the start index
      start = Math.max(start, charIndexMap[char] + 1);
    }
    // Update the index of the current character
    charIndexMap[char] = end;
    // Update the maximum length of the substring
    maxLength = Math.max(maxLength, end - start + 1);
  }

  return maxLength;
}

// Example usage:
console.log(lengthOfLongestSubstring("abcabcbb")); // Output: 3 (substring "abc")
console.log(lengthOfLongestSubstring("bbbbb")); // Output: 1 (substring "b")
console.log(lengthOfLongestSubstring("pwwkew")); // Output: 3 (substring "wke")
```

In this solution:

- We use two pointers, `start` and `end`, to define the current substring.
- We use a hash map `charIndexMap` to store the index of each character in the substring.
- As we iterate through the string `s`, we update the `start` pointer when encountering a repeating character, and update the maximum length of the substring (`maxLength`).
- The time complexity of this solution is O(n), where n is the length of the input string `s`, as we iterate through the string only once. The space complexity is O(min(m, n)), where m is the size of the character set.
