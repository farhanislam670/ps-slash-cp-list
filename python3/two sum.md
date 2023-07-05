# Two Sum

#### Problem Link: https://leetcode.com/problems/two-sum/  


## Approach 1 [Brute Force]

### Solution:

The classic brute force approach. 
* Take an element in the list. Iterate through the rest of the elements to check if the sum matches the target. Rinse and repeat.
* The inner loop starts from the element after the current element in the outer loop. By initializing `j` to `i + 1`, we ensure that we don't recheck the elements that have already been compared in previous iterations of the outer loop.

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

## Approach 2 [Using a set]


