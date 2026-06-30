# Triangle 2D

`Problem` - Given a triangle array, return the minimum path sum from top to bottom.

For each step, you may move to an adjacent number of the row below. More formally, if you are on index i on the current row, you may move to either index i or index i + 1 on the next row.

`Example 1:`

Input: triangle = [[2],[3,4],[6,5,7],[4,1,8,3]] <br/>
Output: 11<br/>
Explanation: The triangle looks like: <br/>
2 <br/>
3 4 <br/>
6 5 7 <br/>
4 1 8 3 <br/>
The minimum path sum from top to bottom is 2 + 3 + 5 + 1 = 11 (underlined above).

```C#
    internal class Program
    {
        static void Main(string[] args)
        {
            int[][] triangle = [[-10]];
            int n = triangle.Length;
            int[][] dp = new int[n][];

            for (int i = 0; i < n; i++)
            {
                dp[i] = new int[triangle[i].Length];
                for (int j = 0; j < triangle[i].Length; j++)
                {
                    dp[i][j] = -1;
                }
            }

            int result = Triangle(0, 0, n, triangle, dp);
            Console.WriteLine(result);
        }

        public static int Triangle(int i, int j, int n, int[][] triangle, int[][] dp)
        {
            if (i == n - 1)
                return triangle[i][j];

            if (dp[i][j] != -1)
                return dp[i][j];

            int down = triangle[i][j] + Triangle(i + 1, j, n, triangle, dp);
            int diagonal = triangle[i][j] + Triangle(i + 1, j + 1, n, triangle, dp);

            dp[i][j] = Math.Min(diagonal, down);
            return dp[i][j];
        }
    }
```
