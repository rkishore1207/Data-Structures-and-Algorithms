# Frequency Counting

You are given an array nums consisting of positive integers.

Return the total frequencies of elements in nums such that those elements all have the maximum frequency.

The frequency of an element is the number of occurrences of that element in the array.

**Example 1:** <br/>
Input: nums = [1,2,2,3,1,4]<br/>
Output: 4<br/>
Explanation: The elements 1 and 2 have a frequency of 2 which is the maximum frequency in the array.<br/>
So the number of elements in the array with maximum frequency is 4.

**Example 2:**

Input: nums = [1,2,3,4,5]<br/>
Output: 5<br/>
Explanation: All elements of the array have a frequency of 1 which is the maximum.<br/>
So the number of elements in the array with maximum frequency is 5.<br/>

```C#
    public class Solution {
        public int MaxFrequencyElements(int[] nums) {
            Dictionary<int, int> frequencies = new Dictionary<int, int>();
            int maxFrequency = int.MinValue;
            int answer = 0;

            for (int i = 0; i < nums.Length; i++){
                if (frequencies.TryGetValue(nums[i], out int value))
                    frequencies[nums[i]]++;            
                else
                    frequencies.Add(nums[i], 1);

                if (maxFrequency == frequencies[nums[i]]){
                    answer += frequencies[nums[i]];
                }            
                else if (frequencies[nums[i]] > maxFrequency){
                    maxFrequency = frequencies[nums[i]];
                    answer = frequencies[nums[i]];
                }
            }

            // int maxFrequency = frequencies.Max(x => x.Value);
            // int result = frequencies.Where(x => x.Value == maxFrequency).Sum(y => y.Value);
            return answer;
        }
    }
```