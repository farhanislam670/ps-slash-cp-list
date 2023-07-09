# Find Subsequence of Length K With the Largest Sum

#### Problem Link: https://leetcode.com/problems/find-subsequence-of-length-k-with-the-largest-sum/

## Approach 1

### Solution:


```py
class Solution:
    def maxSubsequence(self, nums: List[int], k: int) -> List[int]:
        my_dict = {}
        indexes, res= [], []
        i = 0
        for num in nums:
            my_dict[i] = num
            i += 1
        sorted_dict = dict(sorted(my_dict.items(), key=lambda x: x[1], reverse=True))
        for i, key in enumerate(sorted_dict.keys()):
            if i < k:
                indexes.append(key)
        indexes.sort()
        for index in indexes:
            res.append(nums[index])
        return res
```

### Time Complexity:
* The time complexity of the provided code is `O(nlog(n))`, where n is the length of the `nums` list.
* Constructing my_dict takes `O(n)` time, where `n` is the length of the `nums` list. 
* Sorting `my_dict` using `sorted()` with a custom key function takes `O(nlog(n))` time. 
* The subsequent `for` loop that appends the first `k` keys to the `indexes` list takes `O(k)` time since it iterates at most `k` times.
* Sorting the `indexes` list using `sort()` takes `O(klog(k))` time.
* The final `for` loop that appends the corresponding elements from the `nums` list to the `res` list takes `O(k)` time since it iterates over the `k` indexes.


### Space Complexity:
* The space complexity of the provided code is `O(n)`, where `n` is the length of the `nums` list.

<br>

## Approach 1B [Cleaner code]

### Solution:


```py
class Solution:
    def maxSubsequence(self, nums: List[int], k: int) -> List[int]:
       my_dict = {}
       for i in range(len(nums)):
           my_dict[i] = nums[i]
       sorted_dict = dict(sorted(sorted_dict.items(), key=lambda x: x[1], reverse=True))
       res = list(n.keys())[0: k] 
       res.sort()

       return [nums[i] for i in res]
```

### Time Complexity:



### Space Complexity:
<br>


## Approach 1C [Even cleaner code]

### Solution:


```py
class Solution:
    def maxSubsequence(self, nums: List[int], k: int) -> List[int]:
        s = sorted(enumerate(nums), key=lambda x: x[1])[-k:]
        return [x[1] for x in sorted(s)]
```

### Time Complexity:



### Space Complexity:






