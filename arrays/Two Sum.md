# Two Sum
Given an array of integers `nums` and an integer `target`, return the indices `i` and `j` such that `nums[i] + nums[j] == target` and `i != j`.

You may assume that every input has exactly one pair of indices `i` and `j` that satisfy the condition.

Return the answer with the smaller index first.

### Example 1:
```
Input: 
nums = [3,4,5,6], target = 7

Output: [0,1]
```

# Constraints:

* `2 <= nums.length <= 1000`
* `-10,000,000 <= nums[i] <= 10,000,000`
* `-10,000,000 <= target <= 10,000,000`
* Only one valid answer exists.

# Solution:
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        prev_map = {}

        for i, num in enumerate(nums):
            need = target - num
            if need in prev_map:
                return [prev_map[need], i]
            prev_map[num] = i
```
