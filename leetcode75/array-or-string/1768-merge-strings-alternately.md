# 1768. Merge Strings Alternately

![Easy](https://img.shields.io/badge/Easy-green)

## Problem Statement

You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return the merged string.

### Example 1:
*Input:*
```
word1 = abc
word2 = pqr
```
*Output:*
```
apbqcr
```
*Explanation:*
```
The merged string will be merged as so:

word1:  a   b   c
word2:    p   q   r
merged: a p b q c r
```
### Example 2:
*Input:*
```
word1 = ab
word2 = pqrs
```
*Output:*
```
apbqrs
```
### Example 3:
*Input:*
```
word1 = abcd
word2 = pq
```
*Output:*
```
apbqcd
```

### Constraints:

- $1 <= word1.length, word2.length <= 100$
- `word1` and `word2` consist of lowercase English letters.

## Solution

We are given two strings `word1` and `word2`.

Our task is to merge the strings by adding letters in alternating order, starting with `word1`. If one string is longer than the other, the additional letters must be appended to the end of the merged string.

We must return the merged string that has been formed.

### Approach 1: Two Pointers

**Intuition:**

An intuitive method is to use two pointers to iterate over both strings. Assume we have two pointers, `i` and `j`, with `i` pointing to the first letter of `word1` and `j` pointing to the first letter of `word2`. We also create an empty string result to store the outcome.

We append the letter pointed to by pointer `i` i.e., `word1[i]`, and increment `i` by `1` to point to the next letter of `word1`. Because we need to add the letters in alternating order, next we append `word2[j]` to result. We also increase `j` by `1`.

We continue iterating over the given strings until both are exhausted. We stop appending letters from `word1` when `i` reaches the end of `word1`, and we stop appending letters from `word2` when `j` reaches the end of `word2`.

**Algorithm:**
1. Create two variables, `m` and `n`, to store the length of `word1` and `word2`.
1. Create an empty string variable `result` to store the result of merged words.
1. Create two pointers, `i` and `j` to point to indices of `word1` and `word2`. We initialize both of them to `0`.
1. While `i < m || j < n`:
    - If `i < m`, it means that we have not completely traversed `word1`. As a result, we append `word1[i]` to `result`. We increment `i` to point to next index of `word1`.
    - If `j < n`, it means that we have not completely traversed `word2`. As a result, we append `word2[j]` to `result`. We increment `j` to point to next index of `word2`.
1. Return `result`.

> The `String` class is immutable in java. So we use the mutable `StringBuilder` to concatenate letters to `result`.

**Implementation:**

```java
class Solution {
    public String mergeAlternately(String word1, String word2) {
        int m = word1.length();
        int n = word2.length();
        StringBuilder result = new StringBuilder();
        int i = 0, j = 0;

        while (i < m || j < n) {
            if (i < m) {
                result.append(word1.charAt(i++));
            }
            if (j < n) {
                result.append(word2.charAt(j++));
            }
        }

        return result.toString();
    }
}
```

**Complexity Analysis:**

Here, `m` is the length of `word1` and `n` is the length of `word2`.

- **Time complexity:** $O(m+n)$
    - We iterate over `word1` and `word2` once and push their letters into `result`. It would take $O(Max(m, n))$ time.

- **Space complexity:** $O(1)$
    - Without considering the space consumed by the input strings (`word1` and `word2`) and the output string (`result`), we do not use more than constant space.

### Approach 2: One Pointer

**Intuition:**

To merge the given words, we can also use a single pointer.

Let `i` be the pointer that we'll use. We begin with `i = 0` and progress to the size of the longer word between `word1` and `word2`, i.e., till `i = max(word1.length(), word2.length())`.

As we progress to the size of a longer word, we check each time if `i` points to an index that is in bounds of the words or not. If `i < word1.length()`, we append `word1[i]` to result. Similarly if `i < word2.length()`, we append `word2[i]` to results.

However, if `i` exceeds the length of any word, we don't have any letters to add from that word, so we ignore it and continue adding the letter from the longer word.

**Algorithm:**
1. Create two variables, `m` and `n`, to store the length of `word1` and `word2`.
1. Create an empty string variable `result` to store the result of merged words.
1. Iterate over `word1` and `word2` using a loop running from `i = 0` to `i < max(m, n)` and keep incrementing `i` by `1` after each iteration:
    - If `i < m`, it means that we have not completely traversed `word1`. As a result, we append `word1[i]` to `result`.
    - If `i < n`, it means that we have not completely traversed `word2`. As a result, we append `word2[i]` to `result`.
1. Return `result`.

**Implementation:**

```java
class Solution {
    public String mergeAlternately(String word1, String word2) {
        int m = word1.length();
        int n = word2.length();
        StringBuilder result = new StringBuilder();

        for (int i = 0; i < Math.max(m, n); i++) {
            if (i < m) {
                result.append(word1.charAt(i));
            }
            if (i < n) {
                result.append(word2.charAt(i));
            }
        }

        return result.toString();
    }
}
```

**Complexity Analysis:**

Here, `m` is the length of `word1` and `n` is the length of `word2`.

- **Time complexity:** $O(m+n)$
    - We iterate over `word1` and `word2` once and push their letters into `result`. It would take $O(Max(m, n))$ time.

- **Space complexity:** $O(1)$
    - Without considering the space consumed by the input strings (`word1` and `word2`) and the output string (`result`), we do not use more than constant space.

