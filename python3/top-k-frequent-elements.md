# Top K Frequent Elements

#### Problem Link: https://leetcode.com/problems/top-k-frequent-elements/


## Approach 1 

### Solution:

```py
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        my_dict = {}
        res = []
        N = len(nums)
        for i in range(N):
            if(nums[i] in my_dict):
                my_dict[nums[i]] += 1
            else:
                my_dict[nums[i]] = 1
        sorted_dict = sorted(my_dict.items(), key=lambda item: item[1], reverse=True)
        for item in sorted_dict:
            if k > 0:
                res.append(item[0])
                print(item[1])
                k -= 1
            else:
                break
        return res
```

### Time Complexity:

### Space Complexity:


## Approach 2

### Solution:

```py
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        nums = Counter(nums)
        nums = sorted(nums.items(), key=lambda x: x[1], reverse=True)
        return [x[0] for x in nums[:k]]
```
### Time Complexity:

### Space Complexity:


