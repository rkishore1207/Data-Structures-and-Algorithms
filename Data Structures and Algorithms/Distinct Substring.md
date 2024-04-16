
# Longest Substring Without Repeating Characters
## C Sharp

### Problem
- Given a string s, find the length of the longest substring without repeating characters. 

### Sample Test Cases
`Example 1:`<br>
`Input:` s = "abcabcbb"<br>
`Output:` 3<br>
`Explanation:` The answer is "abc", with the length of 3.<br>

`Example 2:`<br>
`Input:` s = "bbbbb"<br>
`Output:` 1<br>
`Explanation:` The answer is "b", with the length of 1.<br>

`Example 3:`<br>
`Input:` s = "pwwkew"<br>
`Output:` 3<br>
`Explanation:` The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
 

```C#
public class Solution {
    public int LengthOfLongestSubstring(string s) {
        int length = s.Length;
        HashSet<char> distinctSet = new HashSet<char>();
        int temp = 0, i = 0, maxCount = Int32.MinValue;
        if(length <= 0)
            return 0;
        while (i < length)
        {
            if (distinctSet.Contains(s[i]))
            {
                var uniqueSubstring = string.Join("", distinctSet);
                if(uniqueSubstring != null)
                    maxCount = maxCount > uniqueSubstring.Length ? maxCount : uniqueSubstring.Length;
                distinctSet.Clear();
                i = temp + 1;
                temp = i;
            }
            else
            {
                distinctSet.Add(s[i]);
                i++;
            }
        }
        if(distinctSet.Count > 0) 
            maxCount = maxCount > string.Join("", distinctSet).Length ? maxCount : string.Join("", distinctSet).Length;
        return maxCount;
    }
}

```