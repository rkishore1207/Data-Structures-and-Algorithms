# Fibonacci

- Declare a DP array with the given length + 1.
- Check the computed value already present in it.
- Follow the recursion.

> We are doing Overlapping Subproblems

1. Tabulation
2. Memoization

```C#
    internal class Program
    {
        static void Main(string[] args)
        {
            int n = 6;
            int[] dp = new int[n + 1];

            for (int i = 0; i < dp.Length; i++)
                dp[i] = -1;

            int result = Fibonacci(n, dp);
            Console.WriteLine(result);
        }

        public static int Fibonacci(int n, int[] dp)
        {
            if (n <= 1)
                return n;

            if (dp[n] != -1)
                return dp[n];

            dp[n] = Fibonacci(n - 1, dp) + Fibonacci(n - 2, dp);
            return dp[n];
        }

        private static int FibonacciTabulationWithSpace(int n)
        {
            int[] dp = new int[n + 1];
            dp[0] = 0; dp[1] = 1;

            for (int i = 2; i < dp.Length; i++)
            {
                dp[i] = dp[i - 1] + dp[i - 2];
            }

            return dp[n];
        }

        private static int FibonacciTabulationWithoutSpace(int n)
        {
            int prev = 1, prev2 = 0, current = 0;

            for (int i = 2; i <= n; i++)
            {
                current = prev + prev2;
                prev2 = prev;
                prev = current;
            }

            return current;
        }
    }
```
