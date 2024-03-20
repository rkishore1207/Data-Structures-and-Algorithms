
#  Sort An Array of 0s, 1s and 2s

### Problem statement

- You have been given an array/list 'arr' consisting of 'n' elements.
- Each element in the array is either 0, 1 or 2.
- Sort this array/list in increasing order.
- Do not make a new array/list. Make changes in the given array/list.

### Sample Test Cases
- `Example `:
- **Input:** 'arr' = [2, 2, 2, 2, 0, 0, 1, 0]
- **Output:** Final 'arr' = [0, 0, 0, 1, 2, 2, 2, 2]
- **Explanation:** The array is sorted in increasing order.

### DNF Algorithm (Dutch National Flag Algorithm)

- [0,low-1] => Extreme Left => 0's
- [low,mid-1]  => 1's
- [high+1,n-1] => Extreme Right => 2's
- [Refernce Image](image.png)
- If arr[mid] == 0 => swap(arr[mid],arr[low]) => mid++,low++;
- If arr[mid] == 1 => mid++;
- If arr[mid] == 1 => swap(arr[mid],arr[high]) => high--;

```C#
    public class Solution {
    public void SortColors(int[] nums) {
        int low = 0;
        int mid = 0;
        int high = nums.Length - 1;
        int i = 0;
        while(mid <= high){
            int element = nums[i];
            if (element == 0)
            {
                nums[mid] = nums[low];
                nums[low] = element;
                mid++;
                low++;
                i++;
                continue;
            }
            else if (element == 1)
            {
                mid++;
                i++;
                continue;
            }
            else
            {
                nums[mid] = nums[high];
                nums[high] = element;
                high--;
                continue;
            }
        }
    }
}
```