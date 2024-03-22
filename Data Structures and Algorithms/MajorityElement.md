
# Majority Element

### Problem Statement

- Given an array nums of size n, return the majority element.
- The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

- `Example 1`:

- **Input:** nums = [3,2,3]
- **Output:** 3

- `Example 2`:

- **Input:** nums = [2,2,1,1,1,2,2]
- **Output:** 2

### Better Solution

```C#
    public class Solution {
    public int MajorityElement(int[] nums) {
        int n = nums.Length;
        int initial = 1;
        int value = 0;
        Dictionary<int, int> numbers = new Dictionary<int, int>();
        foreach (var num in nums)
        {
            if (!numbers.ContainsKey(num))
            {
                numbers.Add(num, initial);
            }
            else
            {
                numbers[num]++;
            }
        }
       foreach (var num in numbers.Keys)
       {
            if (numbers[num] > n / 2)
            {
                value = num;
                break;
            }
       }
       return value;
    }
}
```

### Optimal Solution => Moore's Voting Algorithm

```C#
    public class Solution {
    public int MajorityElement(int[] nums) {
       int count = 1;
       int element = nums[0];
       foreach(var num in nums){
         if(element == num && count>0){
            count++;
         }
         else if(element != num){
           count--;
           if(count == 0){
                element = num;
                count = 1;
            }
         }
       }
       return element;
    }
}
```
- Moore's Voting Algorithm
![Moore's Voting Algorithm](https://github.com/rkishore1207/Data-Structures-and-Algorithms/assets/163657858/0983de9c-0501-4602-89e5-3ef9a4f12f42)

 