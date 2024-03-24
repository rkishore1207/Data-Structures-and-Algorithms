
# Maximum Subarray
## C Sharp

### Problem
- Given an integer array nums, find the subarray with the largest sum, and return its sum.

### Sample Test Cases
`Example 1:`<br>
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]<br>
Output: 6<br>
Explanation: The subarray [4,-1,2,1] has the largest sum 6.<br>

`Example 2:`<br>
Input: nums = [1]<br>
Output: 1<br>
Explanation: The subarray [1] has the largest sum 1.<br>

`Example 3:`<br>
Input: nums = [5,4,-1,7,8]<br>
Output: 23<br>
Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.<br>
 

```C#
public class Solution {
    public int MaxSubArray(int[] nums) {
        int sum = 0, maxSum = Int32.MinValue;
        for (int i = 0 ; i < nums.Count(); i++){
            sum += nums[i]; //adding all the elements in the array
            maxSum = maxSum > sum ? maxSum : sum; // updating the maximum sum
            if(sum < 0) // changing the sum into zero if it is negative because negative value reduce the total sum
                sum = 0;
        }
        return maxSum;
    }
}
```
* Reference
![Maximum Subarray Sum](https://github.com/rkishore1207/Data-Structures-and-Algorithms/assets/146698138/6997cf6b-ebf5-409f-8837-6bf45ef38401)
