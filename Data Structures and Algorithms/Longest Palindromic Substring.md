
# Largest Palindromic Substring
## C Sharp

### Problem
- Given a string s, return the longest palindromic substring in s.

### Sample Test Cases
`Example 1:` <br>
Input: s = "babad"<br>
Output: "bab"<br>
Explanation: "aba" is also a valid answer.<br>

`Example 2:` <br>
Input: s = "cbbd"<br>
Output: "bb"<br>
 

```C#
public class Solution {
    public string LongestPalindrome(string s) {
        int length = s.Count();
        string maxPalindrome1 = "",maxPalindrome2 = "";
        for(int i=0;i<length;i++){
            int left = i,right = i;
            while(left >= 0 && right < length){
                if(s[left] == s[right]){
                    left--;
                    right++;
                }
                else break;
            }
            string palindrome = "";
            for(int j=left+1;j<=right-1;j++){
                palindrome = palindrome + s[j];
            }
            maxPalindrome1 = maxPalindrome1.Count() > palindrome.Count() ? maxPalindrome1 : palindrome;
        }
        for(int i=0;i<length-1;i++){
            int left = i , right = i+1;
            while(left >= 0 && right < length){
                if(s[left] == s[right]){
                    left--;
                    right++;
                }
                else break;
            }
            string palindrome = "";
            for(int j=left+1;j<=right-1;j++){
                palindrome = palindrome + s[j];
            }
            maxPalindrome2 = maxPalindrome2.Count() > palindrome.Count() ? maxPalindrome2 : palindrome;
        }
        return maxPalindrome1.Count() > maxPalindrome2.Count() ? maxPalindrome1 : maxPalindrome2;
    }
}

```
- Sample Image
![Longest palindromic substring](https://github.com/rkishore1207/Data-Structures-and-Algorithms/assets/146698138/6f8f8c60-15b2-42c4-8d8d-2cbd7efdb855)