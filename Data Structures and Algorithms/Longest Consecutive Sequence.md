
# Longest Consecutive Sequence
## C Sharp

### Problem
- Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.
- You must write an algorithm that runs in O(n) time.

### Sample Test Cases
- `Example 1:`
- **Input:** nums = [100,4,200,1,3,2]
- **Output:** 4
- **Explanation:** The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is **4**.

- `Example 2:`
- **Input:** nums = [0,3,7,2,5,8,4,6,0,1]
- **Output:** 9
 

```C#
public class Solution {
    public int LongestConsecutive(int[] nums) {
        HashSet<int> numbers = new HashSet<int>();
        int maxLength = 0;
        //Copying array into hashset to retain our array order as it was before
        foreach(var number in nums){
            numbers.Add(number);
        }
        for(int i = 0; i < nums.Count(); i++){ // loop over all the elements in the array
            int count = 1;
            // check this condition with all the elements for to find the bottom most digit in the sequence in order to start the count.{from example 1 => other than '100','200','1' every other elements just skip the else part}
            if(numbers.Contains(nums[i]-1)) 
                continue;
            // if next element is found then increment the count and increment that element also, until the next element would not find.
            else{
                int nextNumber = nums[i] + 1;
                while(numbers.Contains(nextNumber)){
                    count++;
                    nextNumber += 1 ;
                }
                // updating the maxLength with the current count vaiable
                maxLength = count > maxLength ? count : maxLength;
            }
        }
        return maxLength;
    }
}
```