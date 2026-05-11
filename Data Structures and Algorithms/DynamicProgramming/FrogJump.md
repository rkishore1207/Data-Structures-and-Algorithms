# Frog Jump

## Problem

- You are given a 0-indexed integer array stones sorted in strictly increasing order representing the positions of stones in a river.

* A frog, initially on the first stone, wants to travel to the last stone and then return to the first stone. However, it can jump to any stone at most once.

* The length of a jump is the absolute difference between the position of the stone the frog is currently on and the position of the stone to which the frog jumps.

* More formally, if the frog is at stones[i] and is jumping to stones[j], the length of the jump is |stones[i] - stones[j]|.
* The cost of a path is the maximum length of a jump among all jumps in the path.

* Return the minimum cost of a path for the frog.

## Example 1

**Input**: stones = [0,2,5,6,7]
**Output**: 5
**Explanation**: The above figure represents one of the optimal paths the frog can take.
The cost of this path is 5, which is the maximum length of a jump.
Since it is not possible to achieve a cost of less than 5, we return it.

## Example 2

**Input**: stones = [0,3,9]
**Output**: 9
**Explanation**:
The frog can jump directly to the last stone and come back to the first stone.
In this case, the length of each jump will be 9. The cost for the path will be max(9, 9) = 9.
It can be shown that this is the minimum achievable cost.

```C#
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] heights = { 2, 3, 4, 2, 4, 7, 8 };
            int[] dp = new int[heights.Length];
            int n = 6;

            for (int i = 0; i < dp.Length; i++)
                dp[i] = -1;

            var minimumEnergy = FrogJump(heights, dp, n);
            Console.WriteLine(minimumEnergy);
        }

        private static int FrogJump(int[] heights, int[] dp, int n)
        {
            if (n == 0)
                return 0;

            if (dp[n] != -1)
                return dp[n];

            int left = FrogJump(heights, dp, n - 1) + Math.Abs(heights[n] - heights[n - 1]);
            int right = n <= 1 ? int.MaxValue : FrogJump(heights, dp, n - 2) + Math.Abs(heights[n] - heights[n - 2]);

            int minimumEnergy = Math.Min(left, right);
            dp[n] = minimumEnergy;

            return minimumEnergy;
        }
    }
```

![Recursive Tree](https://github.com/user-attachments/assets/deca4dfb-a40b-4eab-acf0-05dfc46edc5f)

![Recurrence Relation](https://github.com/user-attachments/assets/bcaccbbe-c17e-4b4f-ba4f-c8eac24675da)
