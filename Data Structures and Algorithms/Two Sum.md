
# Two Sum

### Problem Statement
- Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
- You may assume that each input would have exactly one solution, and you may not use the same element twice.
- You can return the answer in any order.

### Sample Test Cases
- `Example 1`:
- **Input:** nums = [2,7,11,15], target = 9
- **Output:** [0,1]
- **Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

- `Example 2`:
- **Input:** nums = [3,2,4], target = 6
- **Output:** [1,2]

- `Example 3`:
- **Input:** nums = [3,3], target = 6
- **Output:** [0,1]

```C#
    public class Solution {
    public int[] TwoSum(int[] nums, int target) {
        int i = 0;
        //Creating an array of size 2 since we are going to return exactly one pair
        int[] sum = new int[2];
        Dictionary<int,int> hashmap = new Dictionary<int,int>();

        foreach(var num in nums){
            /*Finding the element (i.e) target - the first element in the array = wanted element*/
            var element = target - num;
            //If the element is not present , add the element to hashmap
            if(!hashmap.ContainsValue(element)){
                  hashmap.Add(i,num);
                  //Increment to next index
                  i++;
            }
            else{
                //If it contains find its key in hashmap
                int key = hashmap.FirstOrDefault(x => x.Value == element).Key;
                sum[0] = key;
                sum[1] = i; 
            }
        }
        return sum;
    }
}
```