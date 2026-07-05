# Two-Pointer Optimization Pattern

The Two-Pointer technique optimizes search boundaries by managing two independent index references that move toward each other or in tandem, bypassing the need for nested $O(n^2)$ loops.

### 💡 Core Recognition Strategy
* **Input State:** The linear data structure (array or arraylist) is **sorted** or organized sequentially.
* **Objective:** Locating a pair, triplet, or subarray that satisfies a strict target evaluation.

### 💻 Java Implementation: Two Sum II (Sorted Input)

```java
public int[] twoSumSorted(int[] numbers, int target) {
    int left = 0; // #1
    int right = numbers.length - 1; // #2

    while (left < right) {
        int currentSum = numbers[left] + numbers[right];

        if (currentSum == target) {
            return new int[]{left + 1, right + 1}; // #3
        } else if (currentSum < target) {
            left++; // #4
        } else {
            right--; // #5
        }
    }
    return new int[]{-1, -1};
}
```
1. Initialize the **left pointer** reference at the absolute beginning of the sorted collection (index 0).
2. Initialize the **right pointer** reference at the final terminal index position of the array dataset.
3. The problem constraints dictate a 1-indexed return array output, so we offset our 0-indexed positions by adding `1`.
4. If our combined value falls short of the target value, we increment `left` to pull a larger integer layer into the computation.
5. If our combined value exceeds the target value, we decrement `right` to bring a smaller value scale into the calculation.