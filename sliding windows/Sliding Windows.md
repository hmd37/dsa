# Sliding Windows Explained
### The essence of the Sliding Windows technique:

Find and maintain a subarray (window) of a specific size or condition.
Slide the window to the next position by removing the old element(s) and adding the new element(s). Recompute in O(1) or O(log(k)) time rather than O(k) each time.
Use this approach wherever a rolling or continuous data segment is involved—sums, averages, min/max values, counts of distinct elements, and more.

```python
# Calculate the sum of the first window
sum_of_window = 0
for i in range(0, 10):
    sum_of_window += nums[i]
print("Sum of window 1:", sum_of_window)

# Calculate sums of subsequent windows
for window_index in range(1, 100):
    sum_of_window = sum_of_window - nums[window_index - 1] + nums[window_index + 9]
    print("Sum of window", window_index + 1, ":", sum_of_window)
```

# The Flow of Qi
In the meditation hall, the apprentices must learn to sense the flow of Qi, an invisible energy that moves continuously through the temple. Each moment, a different strength of Qi is felt, recorded as a series of numbers.

Master Qu has set a challenge: Find the most powerful surge of Qi over any K consecutive moments.

Your task is to write a function that, given an array of Qi readings and a number K, finds the maximum sum of any contiguous subarray of size K.

### Example Input:

`qi_readings = [2, 1, 5, 1, 3, 2]
k = 3`
### Example Output 1:
`9`
### Explanation: 
The highest Qi surge across 3 consecutive moments is 5 + 1 + 3 = 9.

### Solution

```python
class Solution:
    def max_qi_surge(qi_readings: list[int], k: int) -> int:
        # Step 1: initial window sum
        window_sum = sum(qi_readings[:k])
        max_sum = window_sum

        # Step 2: slide the window
        for i in range(k, len(qi_readings)):
            window_sum += qi_readings[i]      # add next element
            window_sum -= qi_readings[i - k]  # remove previous element
            
            max_sum = max(max_sum, window_sum)

        return max_sum
```
