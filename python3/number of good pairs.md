# Number of Good Pairs

#### Problem Link: https://leetcode.com/problems/number-of-good-pairs/

## Approach 1

### Solution:

- For each element, you start checking subsequent elements and check their equality. If they're equal, append that pair of indices to the list.
- Return the number of pairs in that list.

```py
class Solution:
    def numIdenticalPairs(self, nums: List[int]) -> int:
        res = []
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] == nums[j]:
                    res.append([i,j])
        return len(res)
```

### Time Complexity:

> The time complexity of this code is `O(n^2)` in the worst case.

- The code uses two nested loops: one loop iterating through `i` from `0` to `len(nums)-1`, and another loop iterating through `j` from `i+1` to `len(nums)-1`.
- In the worst case, when there are no identical pairs in the list, the code will compare all possible pairs, resulting in roughly `O(n^2)` comparisons, where `n` is the length of the `nums` list.

### Space Complexity:

> The space complexity is `O(1)` in the best case and `O(k)` in the worst case, where `k` is the number of identical pairs.

- The code uses a list `res` to store pairs of indices where identical elements are found.
  The number of elements stored in `res` is proportional to the number of identical pairs in the input list `nums`.
- In the worst case, when there are no identical pairs, the size of `res` will be `0`.
