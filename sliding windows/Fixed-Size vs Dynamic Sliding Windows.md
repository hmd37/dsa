# Fixed-Size vs Dynamic Sliding Windows
The fixed-size sliding window is a straightforward application, but often we encounter problems where the window size isn’t fixed but is determined by problem constraints. A classic example is finding the smallest subarray with a sum greater than or equal to a given target.

`nums = [2, 1, 5, 2, 3, 2]
target = 7`
Multiple subarrays of different sizes meet the condition (e.g., [5, 2], [2, 3, 2]), but we seek the smallest one. A brute-force approach checks all subarrays, taking O(n^2) time—impractical for large arrays.

### Dynamic Sliding Window Approach
Instead, let's use a dynamic sliding window in O(n) time. We will use two pointers, left and right, to manage the window’s boundaries, and move through subarrays akin to caterpillars crawling forward.

### Expand & Shrink Strategy

* Expand by moving right to the right until current_sum meets or exceeds target.
* Shrink from the left by incrementing left while maintaining the sum condition, tracking the smallest subarray length found.
* Once current_sum is less than target, we can expand again to the right.

```
left = 0
current_sum = 0
min_length = float('inf')

for right in range(len(nums)):
    current_sum += nums[right]

    # Shrink the window while current_sum >= target
    while current_sum >= target:
        min_length = min(min_length, right - left + 1)
        current_sum -= nums[left]
        left += 1

if min_length == float('inf'):
    print("No subarray found.")
else:
    print("Smallest subarray length:", min_length)
```

# The Candlelight Vigil
At the Faangshui Temple, the apprentices perform a nightly candlelight meditation, where they light a series of candles, one after another, to maintain a perfect balance of illumination. However, too much light disrupts the meditative state, so the total brightness must never exceed a certain limit.

Your task is to find the longest sequence of consecutive candles that can be lit without exceeding the brightness limit `max_brightness`.

Write a function that, given an array of candle brightness levels and a maximum brightness `max_brightness`, finds the longest contiguous sequence that stays within the limit. The brightness values are non-negative integers.

### Example Input:

`candles = [7, 2, 3, 1, 5, 4, 3, 2]
max_brightness = 7`
### Example Output:
`3`
Explanation: The longest valid sequence is [2, 3, 1] (sum = 7, length = 4).

### Solution
```python
class Solution:
    def longest_candles(candles: list[int], max_brightness: int) -> int:
        left = 0
        current_sum = 0
        max_length = 0

        for right in range(len(candles)):
            current_sum += candles[right]

            # shrink window if sum exceeds limit
            while current_sum > max_brightness:
                current_sum -= candles[left]
                left += 1

            # update max length
            max_length = max(max_length, right - left + 1)

        return max_length
```
