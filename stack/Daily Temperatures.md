# Daily Temperatures
You are given an array of integers `temperatures` where `temperatures[i]` represents the daily temperatures on the `ith` day.

Return an array `result` where `result[i]` is the number of days after the `ith` day before a warmer temperature appears on a future day. If there is no day in the future where a warmer temperature will appear for the `ith` day, set `result[i]` to `0` instead.

### Example 1:
```
Input: temperatures = [30,38,30,36,35,40,28]
Output: [1,4,1,2,1,0,0]
```
### Constraints:
* `1 <= temperatures.length <= 1000`.
* `1 <= temperatures[i] <= 100`

# Solution:
```python
def dailyTemperatures(temperatures):
    n = len(temperatures)
    result = [0] * n  # Initialize with 0 (default for no warmer day found)
    stack = []  # Stack to store indices, temperatures at these indices are in decreasing order
    
    for i in range(n):
        # While current temperature is warmer than temperature at stack top
        while stack and temperatures[i] > temperatures[stack[-1]]:
            prev_index = stack.pop()
            result[prev_index] = i - prev_index  # Calculate days difference
        
        # Push current index onto stack
        stack.append(i)
    
    return result
```
