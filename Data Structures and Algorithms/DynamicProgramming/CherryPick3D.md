# Cherry Pick 3D DP

`Example 1:`<br/>
**Input:** grid = [[3,1,1],[2,5,1],[1,5,5],[2,1,1]]<br/>
**Output:** 24<br/>
**Explanation:** Path of robot #1 and #2 are described in color green and blue respectively.<br/>
Cherries taken by Robot #1, (3 + 2 + 5 + 2) = 12.<br/>
Cherries taken by Robot #2, (1 + 5 + 5 + 1) = 12.<br/>
**Total of cherries:** 12 + 12 = 24.<br/>

```C#
    internal class Program
    {
        static void Main(string[] args)
        {
            int[][] cherries = [[1, 0, 0, 0, 0, 0, 1], [2, 0, 0, 0, 0, 3, 0], [2, 0, 9, 0, 0, 0, 0], [0, 3, 0, 5, 4, 0, 0], [1, 0, 2, 3, 0, 0, 6]];
            int n = cherries.Length, m = cherries[0].Length;
            long[ , , ] dp = new long[n, m, m];

            for (int i = 0; i < n; i++)
            {
                for (int j = 0; j < m; j++)
                {
                    for (int k = 0; k < m; k++)
                    {
                        dp[i, j, k] = -1;
                    }
                }
            }

            long result = CherryPickup(0, 0, m - 1, n, m, cherries, dp);
            Console.WriteLine(result);
        }

        public static long CherryPickup(int i, int j1, int j2, int n, int m, int[][] cherries, long[ , , ] dp)
        {
            if (j1 < 0 || j2 < 0 || j1 > m - 1 || j2 > m - 1)
                return int.MinValue;
            if (i == n - 1)
            {
                if (j1 == j2)
                    return cherries[i][j2];
                else 
                    return cherries[i][j1] + cherries[i][j2];
            }

            if (dp[i, j1, j2] != -1)
                return dp[i, j1, j2];

            long max = int.MinValue;

            for (int a = -1; a < 2; a++)
            {
                for (int b = -1; b < 2; b++)
                {
                    if (j1 == j2)
                        max = Math.Max(max, cherries[i][j1] + CherryPickup(i + 1, j1 + a, j2 + b, n, m, cherries, dp));
                    else
                        max = Math.Max(max, cherries[i][j1] + cherries[i][j2] + CherryPickup(i + 1, j1 + a, j2 + b, n, m, cherries, dp));
                }
            }

            dp[i, j1, j2] = max;

            return max;
        }
    }
```

![Cherry Pickup](https://github.com/user-attachments/assets/9f9e964e-ff0d-42f0-a09f-8e40fb3e1627)