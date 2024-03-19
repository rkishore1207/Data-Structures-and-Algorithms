
# Largest Subarray with sum zero
## C Sharp

### Problem
- Given an array having both positive and negative integers. The task is to compute the length of the largest subarray with sum 0.

### Sample Test Cases
`Example 1:`<br>
**Input:**
N = 8<br>
A[] = {15,-2,2,-8,1,7,10,23}<br>
**Output:** `5`<br>
**Explanation:** The largest subarray with
sum 0 will be -2 2 -8 1 7.
 

```C#
public class Solution
    {
        public int maxLen(int[] arr, int n)
        {
            Dictionary<int,int> numbers = new Dictionary<int,int>();
            int sum = 0,maxLength = 0,currentLength = 0;
            for(int i=0;i<arr.Count();i++){
                sum += arr[i];
                if(sum == 0)
                    maxLength = i + 1;
                else{
                    if(!numbers.ContainsKey(sum)){
                        numbers.Add(sum,i);
                    }
                    else{
                        currentLength = i - numbers[sum];
                        maxLength = currentLength > maxLength ? currentLength : maxLength;
                    }
                }
            }
            return maxLength;
        }

    }

```
- Sample Image
![Larget subarray with zero sum](https://github.com/rkishore1207/Data-Structures-and-Algorithms/assets/146698138/43df9b63-fb80-4889-ba1d-90be55f322d3)