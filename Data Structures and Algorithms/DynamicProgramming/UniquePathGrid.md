# Unique Path Grid

`Problem` - Given two integers m and n representing the number of rows and columns of a grid, respectively, find the number of distinct paths from the top-left cell (0, 0) to the bottom-right cell (m - 1, n - 1). From any cell, you can move only right or down.

```C#
    internal class Program
    {
        static void Main(string[] args)
        {
            int m = 3, n = 3;
            int[,] dp = new int[m, n];

            for (int i = 0; i < m; i++)
            {
                for (int j = 0; j < n; j++)
                    dp[i, j] = -1;
            }

            int result = UniquePathGrid(m - 1, n - 1, dp);
            Console.WriteLine(result);
        }

        public static int UniquePathGrid(int i, int j, int[,] dp)
        {
            if (i == 0 && j == 0)
                return 1;
            else if (i < 0 || j < 0)
                return 0;

            int left, top;
            if (dp[i, j] != -1)
                left = dp[i, j];

            if (dp[i, j] != -1)
                top = dp[i, j];

            left = UniquePathGrid(i - 1, j, dp);
            top = UniquePathGrid(i, j - 1, dp);

            return left + top;
        }
    }
```

![Unique Path Grid](https://github.com/user-attachments/assets/d4cf0959-6dc5-4fed-b733-ca0d28c7e9c8)
