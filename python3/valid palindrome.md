# Valid Palindrome

#### Problem Link: https://leetcode.com/problems/valid-palindrome/  


## Approach 1

### Solution:
* Convert all the characters in the string to lowercase where applicable.
* Initialise left and right pointers. 
* While `l` is behind `r`, iterate through the string till the central valid character is reached. 

```py linenums
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = s.lower()
        l,r = 0, len(s)-1
        while l < r: 
            while l < r and not s[l].isalnum():
                l += 1
            while l < r and not s[r].isalnum():
                r -= 1
            if s[l] != s[r]:
                return False 
            l += 1
            r -= 1     
        return True
```

### Time Complexity:
* The time complexity of this code is `O(n)`, where n is the length of the string `s`.

### Space Complexity:
* The space complexity of the solution is `O(1)` because it uses a constant amount of extra space i.e., space for the `l` and `r` pointers that do not depend on the input size.


