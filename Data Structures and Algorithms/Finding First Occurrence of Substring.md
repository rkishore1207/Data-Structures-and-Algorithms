
# Finding First Occurrence of a Substring
## C Sharp

### Problem
- Finding the first occurrence of a patternor substring in a string 

### Sample Test Cases

`Example 1:`<br>
`Input:` haystack = "sadbutsad", needle = "sad"<br> 
`Output:` 0<br>
`Explanation:` "sad" occurs at index 0 and 6.<br>
The first occurrence is at index 0, so we return 0.<br>
`Example 2:`<br>
`Input:` haystack = "leetcode", needle = "leeto"<br>
`Output:` -1<br>
`Explanation:` "leeto" did not occur in "leetcode", so we return -1.<br>
 

```C#
public class Solution {
    public int StrStr(string haystack, string needle) {
        int i=0, j=0 , length1 = haystack.Length, length2 = needle.Length, index = -1;
        while(i < length1 && j < length2)
        {
            if (haystack[i] == needle[j])
            {
                if (index == -1)
                    index = i;
                i++; j++;
            }
            else if (haystack[i] != needle[j])
            {
                if(index != -1)
                    i = index + 1;
                else
                    i++;
                index = -1;
                j = 0;
            }
            else if (j == length2 - 1)
                break;
        }
        if(j < length2)
            return -1;
        return index;
    }
}

```