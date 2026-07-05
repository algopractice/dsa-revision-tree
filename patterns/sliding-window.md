# Sliding Window Core Pattern

The Sliding Window pattern converts nested loops into a single linear pass by maintaining a continuous sub-segment ("window") over an array or string that expands or contracts dynamically based on problem criteria.

### 💡 Core Recognition Strategy
* **Input State:** Problem mentions **contiguous** subarrays, sub-segments, or substrings.
* **Objective:** Finding the maximum, minimum, or optimal longest/shortest window length matching a specific target condition.

### 💻 Java Implementation: Minimum Size Subarray Sum

```java
public int minSubArrayLen(int target, int[] nums) {
    int minLength = Integer.MAX_VALUE;
    int windowSum = 0;
    int left = 0; // #1

    for (int right = 0; right < nums.length; right++) {
        windowSum += nums[right]; // #2

        while (windowSum >= target) { // #3
            minLength = Math.min(minLength, right - left + 1); // #4
            windowSum -= nums[left]; // #5
            left++; // #6
        }
    }
    return minLength == Integer.MAX_VALUE ? 0 : minLength;
}
```
1. Establishes the **left boundary pointer** of our tracking window to manage contraction phases.
2. Dynamically expands the window by absorbing the current element at the **right boundary pointer** into our running summation tracker.
3. Triggers a contraction check loop the moment our current window sum matches or exceeds the required target constraint threshold.
4. Records and isolates the smallest window length found so far by evaluating the current distance between our `right` and `left` index points.
5. Systematically subtracts the element trailing at the `left` index boundary to prepare the window sum for a size contraction.
6. Increments the `left` boundary forward to physically shrink the window size while searching for a more optimal, smaller sub-segment.