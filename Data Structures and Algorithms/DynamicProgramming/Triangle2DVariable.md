# Triangle 2D Variable

```C#
    internal class Program
    {
        static void Main(string[] args)
        {
            int[][] triangle = [[1, 2, 10, 4], [100, 3, 2, 1], [1, 1, 20, 2], [1, 2, 2, 1]];
            int n = triangle.Length;
            int m = triangle[n - 1].Length;
            int[][] dp = new int[n][];

            for (int i = 0; i < n; i++)
            {
                dp[i] = new int[triangle[i].Length];
                for (int j = 0; j < triangle[i].Length; j++)
                {
                    dp[i][j] = -1;
                }
            }

            int maxSum = int.MinValue;
            for (int i = 0; i < triangle[n - 1].Length; i++)
            {
                int value = Triangle(n - 1, i, triangle, dp);
                maxSum = Math.Max(maxSum, value);
            }
            
            Console.WriteLine(maxSum);
        }

        public static int Triangle(int i, int j, int[][] triangle, int[][] dp)
        {
            if (j < 0 || j >= triangle[i].Length)
                return int.MinValue;

            if (i == 0)
                return triangle[i][j];

            if (dp[i][j] != -1)
                return dp[i][j];

            int top = triangle[i][j] + Triangle(i - 1, j, triangle, dp);
            int leftDiagonal = triangle[i][j] + Triangle(i - 1, j - 1, triangle, dp);
            int rightDiagonal = triangle[i][j] + Triangle(i - 1, j + 1, triangle, dp);

            dp[i][j] = Math.Max(top, Math.Max(leftDiagonal, rightDiagonal));

            return dp[i][j];
        }
    }
```