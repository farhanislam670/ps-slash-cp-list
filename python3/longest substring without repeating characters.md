# Longest Substring Without Repeating Characters

#### Problem Link: https://leetcode.com/problems/longest-substring-without-repeating-characters/

## Approach 1

### Solution:

```py
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        left, right, count, maximum = 0, 0, 0, 0
        char_set = set()
        while right < len(s):
            if s[right] in char_set:
                char_set.discard(s[left])
                left += 1
                count -= 1
            else:
                char_set.add(s[right])
                count += 1
                right += 1
                maximum = max(count, maximum)
        return maximum
```

### Time Complexity:

### Space Complexity:

<br>

## Approach 2

### Solution:

```py
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        charSet = set()
        l = 0
        res = 0

        for r in range(len(s)):
            while s[r] in charSet:
                charSet.remove(s[l])
                l += 1
            charSet.add(s[r])
            res = max(res, r - l + 1)
        return res
```

### Time Complexity:

### Space Complexity:
