# Sorted Array Optimization

When an array is sorted, look for patterns that bypass $O(n^2)$ nested loops.

### 💡 Core Pattern: The Binary Search Variant
Use this when you need to locate a specific element boundary or split point in $O(\log n)$ runtime.

```java
public int findMin(int[] nums) {
    int left = 0;
    int right = nums.length - 1;

    while (left < right) {
        int mid = left + (right - left) / 2; // #1

        if (nums[mid] > nums[right]) {
            left = mid + 1; // #2
        } else {
            right = mid; // #3
        }
    }
    return nums[left];
}
```
1. Calculates the mid-point without causing integer overflow errors in high-constraint datasets.
2. If the mid element exceeds the right element, the minimum value *must* reside in the unsearched right half.
3. If the mid element is smaller, the pivot point or minimum element lies on the left side or is the mid element itself.
