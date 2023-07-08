# Divide a String Into Groups of Size k

#### Problem Link: https://leetcode.com/problems/divide-a-string-into-groups-of-size-k/

## Approach 1 

### Solution:
* 

```py
class Solution:
    def divideString(self, s: str, k: int, fill: str) -> List[str]:
        res = []
        i = 0
        while len(s)%k != 0:
            s += fill
        s_length = len(s)
        iterations = s_length//k
        while iterations != 0:
            res.append(s[k*i: k*i+k])
            i += 1
            iterations -= 1
        return res
```

### Time Complexity:

### Space Complexity:
* The space complexity of this solution is `O(n)`, where `n` is the length of the final string `s` after adding the `fill` characters.
<br>

## Approach 1B [Cleaner code] 

### Solution:

```py
class Solution:
    def divideString(self, s: str, k: int, fill: str) -> List[str]:
        
        partitioned = []
        start = 0
        finish = k

        if len(s)%k > 0:
            s = s + fill * (k - len(s)%k)

        while finish <= len(s):
            partitioned.append(s[start:finish])
            start += k
            finish += k
            
        return partitioned
```

### Time Complexity:
* Same as 1A

### Space Complexity:
* Same as 1A