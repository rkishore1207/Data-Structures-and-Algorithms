
# Rotated Sorted Array
## C Sharp

### Problem
- Given the sorted rotated array nums of unique elements, return the minimum element of this array.

### Sample Test Cases

`Example 1:`<br>
`Input:` nums = [3,4,5,1,2]<br>
`Output:` 1<br>
`Explanation:` The original array was [1,2,3,4,5] rotated 3 times.
 

```C#
public class Solution {
    public int FindMin(int[] nums) {
        int temp = nums[0],flag = 0,minValue = 0;
        for(int i = 1; i < nums.Count(); i++)
        {
            if (nums[i] <= temp)
            {
                temp = nums[i];
                minValue = temp;
                flag = 1;
                break;
            }
        }
        if(flag == 0)
        {
            minValue = temp;
        }
        return minValue;
    }
}

```