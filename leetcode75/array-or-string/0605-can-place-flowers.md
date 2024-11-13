# 605. Can place Flowers

![Easy](https://img.shields.io/badge/Easy-green) 
![Array](https://img.shields.io/badge/Array_|_Greedy-blue)

## Problem Statement


### Example 1:
*Input:*
```
```
*Output:*
```
```

### Example 2:
*Input:*
```
```
*Output:*
```
```
> *Explanation:* 

### Example 3:
*Input:*
```
```
*Output:*
```
```

> *Explanation:* 

### Constraints:


## Solution

### Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

### Approach
<!-- Describe your approach to solving the problem. -->

### Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

### Code
```java []
public class LeetCode605 {

    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        int count = 0;
        for (int i = 0; i < flowerbed.length; i++) {
            // Check if the current plot is empty.
            if (flowerbed[i] == 0) {
                // Check if the left and right plots are empty.
                boolean emptyLeftPlot = (i == 0) || (flowerbed[i - 1] == 0);
                boolean emptyRightPlot = (i == flowerbed.length - 1) || (flowerbed[i + 1] == 0);

                // If both plots are empty, we can plant a flower here.
                if (emptyLeftPlot && emptyRightPlot) {
                    flowerbed[i] = 1;
                    count++;
                }
            }
        }
        return count >= n;
    }
}

```