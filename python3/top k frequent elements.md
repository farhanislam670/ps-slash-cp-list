# Top K Frequent Elements

#### Problem Link: https://leetcode.com/problems/top-k-frequent-elements/


## Approach 1 

### Solution:

* Insert the elements of the list into a dictionary and count their frequencies. 
* Sort the dictionary by the values (not the keys) in the descending order. What results is a dictionary that has the the k-most frequent elements at the top of the sorted dictionary. From here, you just need to insert the top k elements from the sorted dictionary into the result array and you're good to go.
* Insert the k-most frequent elements in the result list i.e., the top k elements .

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
                k -= 1
            else:
                break
        # res = [item[0] for item in sorted_dict[:k]]
        # This is a one-liner to insert the elements into the "res" array
        return res
```

### Time Complexity:
> The time complexity of this code is `O(nlog(n))`, where n is the length of the `nums` list.

* Inserting the elements and their respective frequencies takes `O(n)` time as the entire list has to be traversed.
* Sorting the dictionary takes `O(nlog(n))` time.
* Inserting it into the result list takes `O(k)` time.
* The sorting operation is the most dominant factor in this solution and hence it has `O(nlog(n))` time complexity.

### Space Complexity:


## Approach 1B [Optimize 1A]

### Solution:
* The approach is the same as 1A, only here, the code is much cleaner.

```py
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        nums = Counter(nums) # O(n)
        nums = sorted(nums.items(), key=lambda x: x[1], reverse=True) # O(nlog(n))
        return [x[0] for x in nums[:k]] # O(k)
```
### Time Complexity:
* Same as 1A

### Space Complexity:


## Approach 2

### Solution: 
* Insert the elements of the list into a dictionary and count their frequencies. `cnt[n] = cnt.get(n, 0) + 1` achieves initializing and incrementing in a singular line.
* Initialize an array of arrays [specifically list of lists here] where the indices denote the frequencies of the elements whereas the 

```py
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        cnt = {}
        freq = [[] for i in range(len(nums)+1)]
        res = []

        for n in nums:
            cnt[n] = cnt.get(n, 0) + 1
        for n, c in cnt.items():
            freq[c].append(n)

        print(freq) # for visualising what's happening in the array of arrays i.e., the frequency array.
        
        for i in range(len(freq)-1, 0, -1):
            for n in freq[i]:
                res.append(n)
                if len(res) == k:
                    return res
```

### Time Complexity:
* The time complexity of this solution is `O(n)`

### Space Complexity:
