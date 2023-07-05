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

### Space Complexity:


## Approach 2 [In Progress]
### Solution:

```py
def isRobotBounded(self, instructions: str) -> bool:
        my_dict = {
            'L': 0,
            'R': 0,
        }
        for i in instructions:
            if i in my_dict:
                my_dict[i] += 1
    
        if (my_dict['L'] and my_dict['R']) > 0:
            if (my_dict['L'] % 2 == 0 and my_dict['R'] % 2 != 0) or (my_dict['L'] % 2 != 0 and my_dict['R'] % 2 == 0):
                return False

        if my_dict['L'] > 0 and my_dict['R'] == 0:
            return True
    
        if my_dict['R'] > 0 and my_dict['L'] == 0:
            return True
    
        return False
```

### Time Complexity:

### Space Complexity:




