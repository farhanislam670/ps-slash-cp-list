# Robot Bounded In Circle

#### Problem Link: https://leetcode.com/problems/robot-bounded-in-circle/


## Approach 1 

### Solution:

```py
class Solution:
    def isRobotBounded(self, instructions: str) -> bool:
        x, y, dir_pointer = 0, 0, 0
        for i in instructions:
            if i == 'G':
                if dir_pointer == 0:
                    y += 1
                elif dir_pointer == 1:
                    x += 1 
                elif dir_pointer == 2:
                    y -= 1 
                else:
                    x -= 1
            elif i == 'L':
                dir_pointer = (dir_pointer-1)%4
            else: 
                dir_pointer = (dir_pointer+1)%4
        if (dir_pointer == 0) and not (x == 0 and y == 0):
                return False
        else:
            return True
```

### Time Complexity:
* The time complexity of this code is `O(n)` where `n` is the length of the string.

### Space Complexity:





