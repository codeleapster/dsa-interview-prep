# 1431. Kids With the Greatest Number of Candies

![Easy](https://img.shields.io/badge/Easy-green) 
![Array](https://img.shields.io/badge/Array-blue)

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
class Solution {
    public List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        int highest = 0;
        for(int i=0; i<candies.length; i++) {
            highest = Integer.max(candies[i], highest);
        }

        List<Boolean> list = new ArrayList<>();
        for(int i=0; i<candies.length; i++) {
            if(candies[i] + extraCandies >= highest) {
                list.add(true);
            } else {
                list.add(false);
            }
        }
        return list;
    }
}
```