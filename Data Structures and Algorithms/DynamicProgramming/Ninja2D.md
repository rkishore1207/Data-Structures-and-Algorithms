# Ninja 2D

`Problem`

- Ninja is planing this ‘N’ days-long training schedule. Each day, he can perform any one of these three activities. (Running, Fighting Practice or Learning New Moves). Each activity has some merit points on each day. As Ninja has to improve all his skills, he can’t do the same activity in two consecutive days. Can you help Ninja find out the maximum merit points Ninja can earn?

- You are given a 2D array of size N\*3 ‘POINTS’ with the points corresponding to each day and activity. Your task is to calculate the maximum number of merit points that Ninja can earn.

`Example`<br/>
**Input**

- 10 40 70
- 20 50 80
- 30 60 90 <br/>
  **Output**
- One of the answers can be:
- On the first day, Ninja will learn new moves and earn 70 merit points.
- On the second day, Ninja will do fighting and earn 50 merit points.
- On the third day, Ninja will learn new moves and earn 90 merit points.
- The total merit point is 210 which is the maximum.
  Hence, the answer is 210.

```C#
    internal class Program
    {
        static void Main(string[] args)
        {
            int N = 4;
            int[][] task = { [2, 1, 3], [3, 4, 6], [10, 1, 6], [8, 3, 7] };

            int[,] dp = new int[N, 4];
            for (int i = 0; i < N; i++)
            {
                for (int j = 0; j < 4; j++)
                {
                    dp[i, j] = -1;
                }
            }

            int result = Ninja(N - 1, 3, task, dp);
            Console.WriteLine(result);
        }

        public static int Ninja(int day, int last, int[][] task, int[,] dp)
        {
            if (day == 0)
            {
                int max = int.MinValue;
                for (int i = 0; i < 3; i++)
                {
                    if (i != last)
                        max = Math.Max(max, task[0][i]);
                }
                return max;
            }

            if (dp[day, last] != -1)
                return dp[day, last];

            int maxPoints = int.MinValue;
            for (int i = 0; i < 3; i ++)
            {
                if (i != last)
                {
                    int points = task[day][i] + Ninja(day - 1, i, task, dp);
                    maxPoints = Math.Max(maxPoints, points);
                    dp[day, last] = maxPoints;
                }
            }
            return maxPoints;
        }
    }
```

![Ninja](https://github.com/user-attachments/assets/8e573585-d7ff-42ee-9aa6-0ec4e09efb12)
