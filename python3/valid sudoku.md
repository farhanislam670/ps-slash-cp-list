# Valid Sudoku

#### Problem Link: https://leetcode.com/problems/valid-sudoku/

## Approach 1 [Disgusting solution]

### Solution:

```py
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        cnt = {}

        # row validation
        for sub_list in board:
            cnt = collections.Counter(sub_list)
            for(key, value) in cnt.items():
                if value > 1 and key != '.':
                    return False 

        # column validation
        for i in range(9):
            column = []
            for j in range(9):
                column.append(board[j][i])
                cnt = collections.Counter(column)
                for(key, value) in cnt.items():
                    if value > 1 and key != '.':
                        return False

        # box validation
        for row in range(0, 9, 3): 
            for col in range(0, 9, 3):  
                box = []
                for i in range(3):  
                    for j in range(3):
                        box.append(board[row + i][col + j])
                cnt = collections.Counter(box)
                for(key, value) in cnt.items():
                    if value > 1 and key != '.':
                        return False
        return True
```

### Time Complexity:

### Space Complexity:

<br>

## Approach 1B [Cleaner code] 

### Solution:

```py
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        res = []
        for i in range(9):
            for j in range(9):
                element = board[i][j]
                if element != '.':
                    res += [(i, element), (element, j), (i // 3, j // 3, element)]
        
        return len(res) == len(set(res))
```

### Time Complexity:


### Space Complexity: