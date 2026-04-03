# Max Consecutive Ones

You are given a binary array `nums`, return the maximum number of consecutive `1`'s in the array.

## Example 1:
```
Input: nums = [1,1,0,1,1,1]
Output: 3
```

## Constraints:

* `1 <= nums.length <= 100,000`
* `nums[i]` is either `0` or `1`.

## Solution:
```python
class Solution:
    def findMaxConsecutiveOnes(self, nums: List[int]) -> int:
        max_len = 0
        curr = 0

        for right in nums:
            if right == 1:
                curr += 1
                max_len = max(max_len, curr)
            else:
                curr = 0
                
        return max_len
```
