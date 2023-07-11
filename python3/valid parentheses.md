# Valid Parentheses

#### Problem Link: https://leetcode.com/problems/valid-parentheses/  


## Approach 1

### Solution:


```py 
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        for i in range(len(s)):
            if s[i] == '(' or s[i] == '[' or s[i] == '{':
                stack.append(s[i])
            else:
                if len(stack) == 0: # If there are no opening parentheses, there's no need to check anything.
                    return False
                if s[i] == ')' and stack[-1] == '(':
                    stack.pop()
                elif s[i] == ']' and stack[-1] == '[':
                    stack.pop()
                elif s[i] == '}' and  stack[-1] == '{':
                    stack.pop()
                else:
                    return False # Return false if you encounter a closing parentheses without 
        return len(stack) == 0 
```

### Time Complexity:
> The time complexity of this solution is `O(n)`, where `n` is the length of the input string `s`.
* This is because we iterate through each character in the string once.

### Space Complexity:
> The space complexity is `O(n)`. 
* This is because the stack can potentially contain up to `n/2` elements in the worst case.
* Each opening parentheses character ('(', '[', '{') is pushed onto the stack, and each closing parentheses character is matched with and removed from the stack. The stack's size depends on the number of unmatched opening parentheses at any given point.
<br>

## Approach 2

### Solution:


```py 
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        mapping = {'(': ')', '{': '}', '[': ']'}
        
        for char in s:
            if char in mapping:  # opening parentheses
                stack.append(char)
            else:  # closing parentheses
                if not stack or mapping[stack.pop()] != char:
                    return False
        
        return not stack  # If the stack is empty, my string is valid.
```

### Time Complexity:
* Same as 1A

### Space Complexity:
> The space complexity of this solution is `O(n)` as well.
* In the worst case, if all opening brackets are present in the input string, the stack can contain up to `n/2` elements. Therefore, the space required by the stack is proportional to the length of the input string.


