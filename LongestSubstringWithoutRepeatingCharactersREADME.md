# leet-day31


# Longest Substring Without Repeating Characters

## Problem Statement

Given a string `s`, you need to find the length of the longest substring without repeating characters.

## Example

### Input

```
s = "abcabcbb"
```

### Output

```
3
```

## Approach

To solve this problem, we can use the sliding window technique along with a hash set to keep track of characters in the current substring. We'll maintain two pointers, `left` and `right`, which represent the start and end of the current substring. We'll move the `right` pointer to expand the window and add characters to the hash set. If we encounter a repeating character, we'll move the `left` pointer to the right to shrink the window and remove characters from the hash set until the repeating character is no longer in the substring. The maximum length of the substring without repeating characters will be the answer.

## Algorithm

1. Initialize two pointers, `left` and `right`, both starting at index 0.
2. Initialize an empty hash set to keep track of characters in the current substring.
3. Initialize a variable `maxLength` to store the maximum length of the substring without repeating characters.
4. Iterate through the string `s` using the `right` pointer:
   - If the character at index `right` is not in the hash set, add it to the hash set and update `maxLength` if needed.
   - If the character at index `right` is already in the hash set, remove the character at index `left` from the hash set and increment the `left` pointer.
5. After the iteration, return `maxLength`.

## Complexity Analysis

- Time complexity: O(n), where n is the length of the string.
- Space complexity: O(min(n, k)), where n is the length of the string and k is the size of the character set.

## Implementation

Here's the implementation of the approach in C++:

```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int n = s.length();
        unordered_set<char> charSet;
        int maxLength = 0, left = 0, right = 0;
        
        while (right < n) {
            if (charSet.find(s[right]) == charSet.end()) {
                charSet.insert(s[right]);
                maxLength = max(maxLength, right - left + 1);
                right++;
            } else {
                charSet.erase(s[left]);
                left++;
            }
        }
        
        return maxLength;
    }
};
```
