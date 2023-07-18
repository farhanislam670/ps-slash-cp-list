# Valid Sudoku

#### Problem Link: https://leetcode.com/problems/valid-sudoku/

## Approach 1 [Disgusting solution]

### Solution:

- Initialise a dictionary i.e., `cnt` to count the frequency of elements in lists.
- After that, perform validation checks on each row, column and box such that no valid value i.e., values which are not '.' in each row is repeated, albeit a very cumbersome and unintuitive approach.

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

> The time complexity of this solution is `O(1)`.

### Space Complexity:

> The space complexity of the provided code is `O(1)`.

<br>

## Approach 1B [Cleaner code]

### Solution:

-

```py
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        cols = collections.defaultdict(set)
        rows = collections.defaultdict(set)
        squares = collections.defaultdict(set)  # key = (r//3, c//3)

        for r in range(9):
            for c in range(9):
                if board[r][c] == ".":
                    continue
                if (
                    board[r][c] in rows[r]
                    or board[r][c] in cols[c]
                    or board[r][c] in squares[(r // 3, c // 3)]
                ):
                    return False
                cols[c].add(board[r][c])
                rows[r].add(board[r][c])
                squares[(r // 3, c // 3)].add(board[r][c])
        return True
```

### Time Complexity:

> The time complexity of this solution is `O(1)`.

### Space Complexity:

> The space complexity of the provided code is `O(1)`.

<br>

## Approach 1C [Cleanest code]

### Solution:

- Instead of validating each row, column and box one-by-one why not just store the three positional information of each element all at once and check their uniqueness later?
- If the element is valid, store `(row_number, element)`, `(column_number, element)` and `(box_row_number, box_column_number, element)`.
- Each of these tuples have to be unique and therefore the length of the list and the length of the list when converted to a set should be equal for a valid board.

> Learn how to implement this in C++ and JavaScript

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

> The time complexity of this solution is `O(1)`.

### Space Complexity:

> The space complexity of the provided code is `O(1)`.
