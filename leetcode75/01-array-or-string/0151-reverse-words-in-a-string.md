# 151. Reverse Words in a String
![Easy](https://img.shields.io/badge/Medium-orange) 
![Array](https://img.shields.io/badge/Array_|_Two_Pointers-blue)

## Problem Statement

Given an input string `s`, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in `s` will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

Note that s may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

### Example 1:
*Input:*
```
s = "the sky is blue"
```
*Output:*
```
"blue is sky the"
```

### Example 2:
*Input:*
```
s = "  hello world  "
```
*Output:*
```
"world hello"
```
> *Explanation:* Your reversed string should not contain leading or trailing spaces.
### Example 3:
*Input:*
```
s = "a good   example"
```
*Output:*
```
"example good a"
```

> *Explanation:* You need to reduce multiple spaces between two words to a single space in the reversed string.

### Constraints:
- $1 <= s.length <= 10^4$
- `s` contains English letters (upper-case and lower-case), digits, and spaces ' '.
- There is **at least one** word in `s`.

---

### Solution using Java in-built libraries:

```java
public class Solution {
    public String reverseWords(String s) {
        String[] words = s.split(" ");
        StringBuilder sb = new StringBuilder();
        for (int i = words.length - 1; i >= 0; i--) {
            if (words[i] != null && !words[i].isEmpty()) {
                sb.append(words[i]).append(" ");
            }
        }
        return sb.toString().trim();
    }
}
```


### Solution using Two Pointers:

**Intution:**

1. **Removing leading and trailing spaces**: Begin by trimming the string.
2. **Using two pointers**: One pointer `start` finds the beginning of each word, and the other `end` finds the `end` of the word.
3. **Reversing the words**: insert each word at the begining of the result so as to reverse the words.

**Pseudo Code:**

```
FUNC REVERSE_WORDS(VAR input)
    SET input = input.trim()
    VAR start = 0
    VAR end = 0
    VAR sb as stringbuilder = ""

    FOR i = 0 to n
        SET start = i
        
        WHILE i < n AND charAt(i) != ' '
            i++
        ENDWHILE
        
        SET end = i

        VAR word = input.substring(start, end)
        sb = word + " " + sb

        WHILE i < n AND charAt(i) == ' '
            i++
        ENDWHILE
    ENDFOR
END
```

**Code Implementation:**

```java
public class Solution {
    public String reverseWords(String input) {
        // trim trailing and leading spaces
        input = input.trim();
        StringBuilder sb = new StringBuilder();
        int i = 0;
        int start = 0;
        int end = 0;
        while (i < input.length()) {
            start = i;
            // find end of the word
            while (i < input.length() && input.charAt(i) != ' ') {
                i++;
            }
            end = i;

            String word = input.substring(start, end);
            sb.insert(0, " "); // add space between words
            sb.insert(0, word); // insert word at the beginning to maintain reverse order

            // skip the spaces between the words
            while (i < input.length() && input.charAt(i) == ' ') {
                i++;
            }
        }
        return sb.toString().trim();
    }
}
```

**Explanation:**

1. **Trimming the String**: First, we remove leading and trailing spaces using `trim()`. This ensures we don't have to handle edge cases with unnecessary spaces.
  
2. **Two Pointers**:
   - **`start` pointer**: For each word, `start` is at the i
   - **`end` pointer**: It starts from the begining of the string and moves forward until a space is encountered.
  
3. **Building the Result**: Once a word is identified, it is appended to the result string with a space following it. After processing all words, we strip any extra trailing space.

4. **Return the Final String**: We return the final reversed string, making sure to trim any final extra space.

**Time Complexity:**
- **Time Complexity**: $O(n)$, where `n` is the length of the string. We iterate through the string once, and each word is processed at most once.
- **Space Complexity**: $O(n)$ for the space used by the `StringBuilder` to store the result.
