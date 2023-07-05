# Contains Duplicate

#### Problem Link: https://leetcode.com/problems/contains-duplicate/


## Approach 1 [Brute Force]

### Solution:

Sort the list. If two consecutive values are equal, the list contains a duplicate.

```py
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        nums.sort()
        for i in range(len(nums)-1):
            if nums[i] == nums[i+1]:
                return True
        return False
```

### Time Complexity:
* The code starts by sorting the `nums` list using the `sort()` method, which has a time complexity of `O(n*log(n))` in the average case.
* Looping through the list in the worst case scenario takes `O(n)` time complexity which is overshadowed by `O(n*log(n))`.
* Hence, this solution has a time complexity of `O(n*log(n))`.

### Space Complexity:
* The only space used is for the input list nums. The sorting operation `nums.sort()` is performed in-place.
* The space complexity is therefore `O(1)` as no additional memory is required.
<br>

## Approach 2 [Using a HashSet]

### Solution:


```py
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        hashset = set()
        for n in nums:
            if n in hashset:
                return True
            hashset.add(n)
        return False
```

### Time Complexity:
* In the worst case, the space complexity will be `O(n)`. This is when the list is entirely unique so the entire list has to be traversed.

### Space Complexity:
* The use of a hashset makes this solution consume extra memory. 
* In the worst case, the space complexity will be `O(n)`. This is when the list is entirely unique so each element of that list will be inserted into this hashset.

