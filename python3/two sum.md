# Two Sum

#### Problem Link: https://leetcode.com/problems/two-sum/  


## Approach 1 [Brute Force]

### Solution:

The classic brute force approach. 
* Take an element in the list. Iterate through the rest of the elements to check if the sum matches the `target`. Rinse and repeat.
* The inner loop starts from the element after the current element in the outer loop. By initializing `j` to `i + 1`, we ensure that we don't recheck the elements that have already been compared in previous iterations of the outer loop. A small optimization, even if it's for such an unsightly method.

```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i,j] 
```

### Time Complexity:
> The time complexity of the given solution is `O(n^2)`, where `n` is the length of the input `nums` list.

* The function uses a nested loop to iterate over the elements in the `nums` list. The outer loop iterates through the entire list, and the inner loop iterates from `i+1` till te end of the list.
* Since each loop iterates through the entire remaining part of the list, the total number of iterations will be approximately $$(n-1) + (n-2) + ... + 1 = {n(n-1)\over 2}$$ which is in the order of `n^2`.

### Space Complexity:
> The space complexity of the given solution is `O(1)`.

## Approach 2 [Using a Hashmap]

### Solution:
* Instead of brute forcing it, initialize a hash map. 

```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hash_map = {}
        for i in range(len(nums)):
            if target - nums[i] in hash_map:
                return [hash_map[target-nums[i]], i]
            else: 
                hash_map[nums[i]] = i
```
### Time Complexity:
> The time complexity of this code is `O(n)`, `n` being the number of elements in the `nums` list.

* In this code, a dictionary [hash_map] is used to store the elements of the nums list and their corresponding indices. The code iterates through each element in the `nums` list once using the for loop, resulting in `O(n)` iterations.
* This lookup operation has an average time complexity of `O(1)` for a dictionary.

### Space Complexity:
> The space complexity of the solution is `O(n)`, where `n` is the length of the input `nums` list.

* The function uses a hash map [hash_map] to store previously encountered numbers and their corresponding indices. The space occupied by the hash map scales with the number of unique elements in the `nums` list.
* In the worst case scenario, where all elements in nums are distinct, the hash map will store all `n` elements, resulting in `O(n)` space complexity.

