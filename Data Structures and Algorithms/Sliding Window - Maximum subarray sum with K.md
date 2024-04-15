
# Maximum Subarray sum with K - Sliding Window
## C Sharp

### Problem
- Given an array of integers and a number k, find the maximum sum of a subarray of size k. 

### Sample Test Cases
`Input  :` arr[] = {100, 200, 300, 400},  k = 2<br>
`Output :` 700<br>
<br>

`Input  :` arr[] = {1, 4, 2, 10, 23, 3, 1, 0, 20}, k = 4 <br>
`Output :` 39<br>
`Explanation:` We get maximum sum by adding subarray {4, 2, 10, 23} of size 4.<br>
 

```C#
class Solution
{
    public long maximumSumSubarray(int K, List<int> Arr , int N)
    {
        int temp = 0, i = 0, sum = 0, maxSum = Int32.MinValue ,count = 0;
        while (i < N)
        {
            sum += Arr[i];
            count++;
            if (count == K)
            {
                maxSum = maxSum > sum ? maxSum : sum;
                i = temp + 1;
                temp = i;
                sum = 0;
                count = 0;
                if(temp > N-K)
                    break;
            }
            else
                i++;
        }
        return maxSum; 
    }
}

```