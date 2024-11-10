# 283. Move Zeroes
![Easy](https://img.shields.io/badge/Easy-green) 
![Array](https://img.shields.io/badge/Array_|_Two_Pointers-blue)

## Problem Statement

Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

**Note** that you must do this in-place without making a copy of the array.

### Example 1:
*Input:*
```
nums = [0,1,0,3,12]
```
*Output:*
```
[1,3,12,0,0]
```
### Example 2:
*Input:*
```
nums = [0]
```
*Output:*
```
[0]
```
### Constraints:
- $1 <= nums.length <= 10^4$
- $-2^{31} <= nums[i] <= 2^{31} - 1$


**Follow up:** Could you minimize the total number of operations done?

## Solution

This question comes under a broad category of "Array Transformation". This category is the meat of tech interviews. Mostly because arrays are such a simple and easy to use data structure. Traversal or representation doesn't require any boilerplate code and most of your code will look like the Pseudocode itself.

The 2 requirements of the question are:
- Move all the 0's to the end of array.
- All the non-zero elements must retain their original order.

It's good to realize here that both the requirements are mutually exclusive, i.e., you can solve the individual sub-problems and then combine them for the final solution.

### Approach 1: Brute force

**Intuition**
Traverse the `nums` list first to count the number of zeroes. Then traverse the `nums` list again to store all non-zero elements in ans.

**Algorithm**

**Implementation:**

```java
public class Solution {
    
    public void moveZeroes(int[] nums) {
        
    }
}
```

**Complexity Analysis:**
    
- **Time complexity:**

- **Space complexity:** 


### Approach 2: 

**Intuition**

**Algorithm**

**Implementation:**

```java
public class Solution {
    
    public void moveZeroes(int[] nums) {
        int pos = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                nums[pos] = nums[i];
                pos++;
            }
        }

        while (pos < nums.length) {
            nums[pos++] = 0;
        }
    }

}

```

**Complexity Analysis:**
    
- **Time complexity:** $O(n + numOfZeroes)$

- **Space complexity:** $O(1)$

### Approach 3: 

**Intuition**

**Algorithm**

**Implementation:**

```java
public class Solution {

    public void moveZeroes(int[] nums) {
        int j = 0;
        for (int i = 0; i < nums.length; i++) {
            // If array at i index is not zero then swap and increment j by one
            if (nums[i] != 0) {
                int x = nums[i];
                nums[i] = nums[j];
                nums[j] = x;
                j++;
            }
        }
    }
}

```

**Complexity Analysis:**
    
- **Time complexity:** $O(n)$

- **Space complexity:** $O(1)$
