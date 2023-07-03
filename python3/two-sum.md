# Two Sum

#### Problem Link: https://leetcode.com/problems/two-sum/  


## Approach 1 [Brute Force]

### Solution:
```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i,j] 
```

### Time Complexity:

### Space Complexity:

## Approach 2 


