# Concatenation of Array

#### Problem Link: https://leetcode.com/problems/concatenation-of-array/

## Approach 1

### Solution:

```py
class Solution:
    def getConcatenation(self, nums: List[int]) -> List[int]:
        n = len(nums)
        for i in range(n):
            nums.append(nums[i])
        return nums
```

### Time Complexity:

### Space Complexity:

<br>
