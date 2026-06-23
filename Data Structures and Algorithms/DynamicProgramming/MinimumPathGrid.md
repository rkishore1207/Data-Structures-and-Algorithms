# Minimum Path Grid

- Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

Input: grid = [[1,3,1],[1,5,1],[4,2,1]] <br/>
Output: 7 <br/>
Explanation: Because the path 1 → 3 → 1 → 1 → 1 minimizes the sum.

```C#
public class Solution {
    public int MinPathSum(int[][] grid) {
        int[,] dp = new int[grid.Length, grid[0].Length];

        for (int i = 0; i < grid.Length; i++){
            for (int j = 0; j < grid[0].Length; j++){
                dp[i,j] = -1;
            }
        }

        return MinimuPathSum(grid.Length - 1, grid[0].Length - 1, grid, dp);
    }

    public static int MinimuPathSum(int i, int j, int[][] grid, int[,] dp){
        if (i == 0 && j == 0)
            return grid[i][j];
        if (i < 0 || j < 0)
            return int.MaxValue;
        if (dp[i,j] != -1)
            return dp[i,j];
        int left = MinimuPathSum(i - 1, j, grid, dp);
        int right = MinimuPathSum(i, j - 1, grid, dp);
        dp[i,j] = grid[i][j] + Math.Min(left, right);

        return dp[i,j];
    }
}
```

![Minimum Path grid](https://github.com/user-attachments/assets/4c4dfcfe-0c66-4d86-9a59-20579adc8d90)
