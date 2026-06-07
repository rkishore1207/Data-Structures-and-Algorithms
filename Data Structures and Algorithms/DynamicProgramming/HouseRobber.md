# House Robber

- You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

- Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

**Example 1:**

- **Input**: nums = [1,2,3,1]
- **Output**: 4
- **Explanation**: Rob house 1 (money = 1) and then rob house 3 (money = 3).
  Total amount you can rob = 1 + 3 = 4.

**Example 2:**

- **Input:** nums = [2,7,9,3,1]
- **Output:** 12
- **Explanation:** Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
  Total amount you can rob = 2 + 9 + 1 = 12.

```C#
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] numbers = {2, 7, 3, 1, 4, 2, 1, 8};
            List<int> dp = new List<int>();
            dp.Add(numbers[0]);

            for (int i = 1; i < numbers.Length; i++ )
                dp.Add(-1);

            int result = HouseRobber(numbers, dp, numbers.Length - 1);

            Console.WriteLine(result);
        }

        private static int HouseRobber(int[] numbers, List<int> dp, int n)
        {
            if (n < 0)
                return 0;

            if (dp[n] != -1)
                return dp[n];

            int pick = numbers[n] + HouseRobber(numbers, dp, n - 2);
            int notPick = HouseRobber(numbers, dp, n - 1);

            dp[n] = Math.Max(pick, notPick);
            return dp[n];
        }
    }
```

![Image](https://github.com/user-attachments/assets/b1bd8105-ae67-4f5b-929c-3eacc97d46cb)

![Tree](https://github.com/user-attachments/assets/ec2bfced-8c63-4599-96cc-f787abd7033b)
