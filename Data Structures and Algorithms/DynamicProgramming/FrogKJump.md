# FrogKJump

```C#
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] heights = { 2, 3, 4, 2, 4, 7, 8 };
            int[] dp = new int[heights.Length];
            int n = 6;
            int k = 5;

            for (int i = 0; i < dp.Length; i++)
                dp[i] = -1;

            //var minimumEnergy = FrogKJump(heights, dp, n, k);
            var minimumEnergy = FrogJumpForLoop(dp, heights, k);
            Console.WriteLine(minimumEnergy);
        }

        private static int FrogKJump(int[] heights, int[] dp, int n, int k)
        {
            if (n == 0) return 0;

            if (dp[n] != -1) return dp[n];

            int minimumEnergy = int.MaxValue;

            for (int i = 1; i < k; i++)
            {
                if ((n - i) >= 0)
                {
                    int energy = FrogKJump(heights, dp, n - i, k) + Math.Abs(heights[n] - heights[n - i]);
                    minimumEnergy = Math.Min(minimumEnergy, energy);
                }
            }

            return minimumEnergy;
        }

        private static int FrogJumpForLoop(int[] dp, int[] heights, int k)
        {
            dp[0] = 0;
            int minimumEnergy = 0;
            for (int i = 1; i < heights.Length; i++)
            {
                minimumEnergy = int.MaxValue;
                for (int j = 1; j < k; j++)
                {
                    if (i - j >= 0)
                    {
                        int jump = dp[i - j] + Math.Abs(heights[i] - heights[i - j]);
                        minimumEnergy = Math.Min(minimumEnergy, jump);
                    }
                }

                dp[i] = minimumEnergy;
            }
            return minimumEnergy;
        }
    }
```
