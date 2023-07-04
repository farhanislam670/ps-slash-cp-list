# Find the Prefix Common Array of Two Arrays

#### Problem Link: https://leetcode.com/problems/find-the-prefix-common-array-of-two-arrays/  


## Approach 1 

### Solution:

```py
class Solution:
    def findThePrefixCommonArray(self, A: List[int], B: List[int]) -> List[int]:
        N = len(A)
        frequency = {}
        C = []
        common = 0
    
        for i in range(N):
            if A[i] in frequency:
                frequency[A[i]] += 1
                if frequency[A[i]] == 2:
                    common += 1
            else:
                frequency[A[i]] = 1
        
            if B[i] in frequency:
                frequency[B[i]] += 1
                if frequency[B[i]] == 2:
                    common += 1
            else:
                frequency[B[i]] = 1
        
            C.append(common)
    
        return C
```

### Time Complexity:

### Space Complexity:



