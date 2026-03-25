# Binary Search
Yes, you read that right — binary search can be seen as an index pointers problem. It’s an algorithm that uses pointers (indexes) to locate a target value in a sorted array efficiently. These pointers mark the boundaries of the search space, and at each step, you check the midpoint to decide which half of the array to explore next.

### Intuition behind binary search
Imagine searching for a specific page in a book:

* Open roughly in the middle.
* Check if the target page is earlier or later than where you opened.
* Move left or right, halving the search area until you find the page. Binary search applies this same strategy to an array, repeatedly dividing the problem space in half.

This is a simple example, but binary search can handle much larger arrays and more complex search conditions. Putting it into code, you get:

```
low = 0
high = len(nums) - 1

while low <= high:
    mid = (low + high) // 2
    if nums[mid] == target:
        return mid
    elif nums[mid] < target:
        low = mid + 1
    else:
        high = mid - 1

return -1  # Target not found
```

# The Scroll of Greater Wisdom
Deep within the Faangshui Temple’s library, the apprentices are tasked with finding the next scroll that contains greater wisdom than a given passage. The scrolls are meticulously arranged in ascending order, and the apprentices must use their skills in binary search to locate the right one.

Your task is to find the first scroll (element) in a sorted array that is greater than the given target. Return the scroll if it exists, or -1 if none exists.

### Example Input:
```
scrolls = [2, 3, 5, 7, 11, 13]
target = 6
```

### Expected Output:
`7`

### Solution
```python
class Solution:
    def next_greater_scroll(scrolls: list[int], target: int) -> int:
        low = 0
        high = len(scrolls) - 1
        result = -1

        while low <= high:
            mid = (low + high) // 2
            
            if scrolls[mid] > target:
                result = scrolls[mid]
                high = mid - 1
            else:
                low = mid + 1
            
        return result
```













