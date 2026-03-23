## Fast and Slow Pointers
Fast and slow pointers are a clever technique for working with arrays or linked structures. They move at different speeds to tackle a range of problems—everything from detecting cycles to in-place array modifications.

### Example: Removing Duplicates in a Sorted Array
Task: remove duplicates while keeping all unique elements at the beginning.

```
slow = 0
for fast in range(1, len(nums)):
    if nums[fast] != nums[slow]:
        slow += 1
        nums[slow] = nums[fast]
```

### How It Works

- **Fast pointer:** Scans through every element in the array.
- **Slow pointer:** Keeps track of where the next unique element should be placed.
- **Writing unique values:**  
  Each time `nums[fast]` is different from `nums[slow]`, move `slow` forward and store `nums[fast]` there.

By the time you finish iterating:

- All unique elements are compacted at the front of the array.
- `slow` indicates the index of the last unique element.

- **Time Complexity:** `O(n)` (single pass)
- **Space Complexity:** `O(1)` (in-place)

## The Flowing Stream
The apprentices are tasked with arranging water urns in a line, where empty urns (0) must be moved to the back while keeping the filled urns in their original order. "The stream flows smoothly when the empty spaces are cleared," says Master Qu.

Your task is to write a function that moves all zeros in an array to the end while maintaining the relative order of the non-zero elements.

### Example Input

```array = [0, 1, 0, 3, 12]```
### Expected Output

```[1, 3, 12, 0, 0]```

### Solution

```python
class Solution:
    def move_zeros_to_end(arr):
        slow = 0

        for fast in range(1, len(arr)):
            if arr[fast] != 0:
                arr[slow], arr[fast] = arr[fast], arr[slow]
                slow += 1
    
        return arr
```

