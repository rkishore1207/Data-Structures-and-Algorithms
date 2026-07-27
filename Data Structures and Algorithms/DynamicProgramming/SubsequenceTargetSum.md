# Subsequence Target Sum

- Given an array arr and target sum k, check whether there exists a subsequence such that the sum of all elements in the subsequence equals to k.

Input: arr = [10, 1, 2, 7, 6, 1, 5], k = 8.<br/>
Output: true<br/>
Explanation: Subsequences like [2, 6], [1, 7] sum upto 8<br/>

Input: arr = [2, 3, 5, 7, 9], k = 100. <br/>
Output: false<br/>
Explanation: No subsequence can sum upto 100<br/>

```C#
internal class Program
{
    static void Main(string[] args)
    {
        int[] subsequences = { 4, 1, 1, 1 };
        int[][] dp = new int[subsequences.Length][];
        int target = 8;

        for (int i = 0; i < dp.Length; i++)
        {
            dp[i] = new int[target + 1];
            for (int j = 0; j < dp[i].Length; j++)               
                dp[i][j] = -1;                
        }

        bool result = SubsequenceTarget(subsequences.Length - 1, target, subsequences, dp);
        Console.WriteLine(result);
    }

    public static bool SubsequenceTarget(int index, int target, int[] subsequences, int[][] dp)
    {
        if (target == 0)
            return true;

        if (index == 0)
        {
            if (subsequences[index] - target == 0) return true;
            else return false;
        }

        if (dp[index][target] != -1)
        {
            if (dp[index][target] == 0)
                return false;
            else return true;
        }                

        bool notTake = SubsequenceTarget(index - 1, target, subsequences, dp);
        bool take = false;
        if (subsequences[index] < target)
        {
            take = SubsequenceTarget(index - 1, target - subsequences[index], subsequences, dp);
        }

        if (notTake || take)
            dp[index][target] = 1;
        else dp[index][target] = 0;

        return notTake || take;
    }
}
```