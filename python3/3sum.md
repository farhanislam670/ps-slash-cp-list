# 3Sum

#### Problem Link: https://leetcode.com/problems/3sum/

## Approach 1 [The optimal solution]

### Solution:

```py
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        res = []

        for i, a in enumerate(nums):
            if i > 0 and nums[i - 1] == a:
                continue

            l, r = i + 1, len(nums) - 1
            while l < r:
                sum = nums[i] + nums[l] + nums[r]
                if sum > 0:
                    r -= 1
                elif sum < 0:
                    l += 1
                else:
                    res.append([a, nums[l], nums[r]])
                    l += 1
                    while nums[l] == nums[l - 1] and l < r:
                        l += 1
        return res
```

### Time Complexity:

> The time complexity of this solution is `O(n^2)`

-

### Space Complexity:

<br>
