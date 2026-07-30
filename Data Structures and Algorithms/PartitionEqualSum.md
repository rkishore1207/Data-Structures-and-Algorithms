# Partition Equal Sum

- Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.

Example 1:<br/>

Input: nums = [1,5,11,5]<br/>
Output: true<br/>
Explanation: The array can be partitioned as [1, 5, 5] and [11].<br/>

Example 2:<br/>

Input: nums = [1,2,3,5]<br/>
Output: false<br/>
Explanation: The array cannot be partitioned into equal sum subsets.<br/>

```C#
internal class Program
{
    static void Main(string[] args)
    {
        int[] subsequences = [1, 2, 3, 5];
        int[][] dp = new int[subsequences.Length][];
        int target = subsequences.Sum() / 2;

        for (int i = 0; i < dp.Length; i++)
        {
            dp[i] = new int[target + 1];
            for (int j = 0; j < dp[i].Length; j++)
                dp[i][j] = -1;
        }

        bool result = PartitionSumEqual(subsequences.Length - 1, target, subsequences, dp);
        Console.WriteLine(result);
    }

    public static bool PartitionSumEqual(int index, int target, int[] subsequences, int[][] dp)
    {
        if (subsequences.Sum() % 2 != 0)
            return false;

        else if (target == 0)
            return true;

        else if (index == 0)
        {
            if (target - subsequences[index] == 0) return true;
            else return false;
        }

        else if (dp[index][target] != -1)
        {
            if (dp[index][target] == 0) return false;
            else return true;
        }

        bool notTake = PartitionSumEqual(index - 1, target, subsequences, dp);
        bool take = false;
        if (target >= subsequences[index])
        {
            take = PartitionSumEqual(index - 1, target - subsequences[index], subsequences, dp);
        }

        if (notTake || take) dp[index][target] = 1;            
        else dp[index][target] = 0;

        return notTake || take;
    }
}
```