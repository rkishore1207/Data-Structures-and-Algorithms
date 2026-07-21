# Spiral Matrix

**Example 1:**<br/>
Input: matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]<br/>
Output: [1,2,3,4,8,12,11,10,9,5,6,7]

```C#
internal class Program
{
    static void Main(string[] args)
    {
        int[][] matrix = [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]];
        var result = SpiralMatrix(matrix);

        foreach ( var i in result )
        {
            Console.Write(i + " ");
        }
    }

    public static List<int> SpiralMatrix(int[][] matrix)
    {
        var result = new List<int>();
        int left = 0, right = matrix[0].Length - 1, top = 0, bottom = matrix.Length - 1;

        while (left <= right && top <= bottom)
        {
            for (int i = left; i <= right; i++)
            {
                result.Add(matrix[top][i]);
            }
            top++;

            for (int i = top; i <= bottom; i++)
            {
                result.Add(matrix[i][right]);
            }
            right--;

            if (top < bottom)
            {
                for (int i = right; i >= left; i--)
                {
                    result.Add(matrix[bottom][i]);
                }
                bottom--;
            }

            if (left < right)
            {
                for (int i = bottom; i >= top; i--)
                {
                    result.Add(matrix[i][left]);
                }
                left++;
            }
        }

        return result;
    }

    //public static List<int> SpiralMatrix(int[][] matrix)
    //{
    //    var result = new List<int>();
    //    int i = 0, j = 0, m = matrix.Length, n = matrix[0].Length;
    //    string direction = "right";

    //    while (true)
    //    {
    //        if (result.Count >= m * n)
    //            break;                

    //        if (i > m - 1 || i < 0 || j > n - 1 || j < 0 || result.Contains(matrix[i][j]))
    //        {
    //            direction = DetermineDirection(direction);

    //            if (i > m - 1)
    //            {
    //                i--;
    //                j--;
    //            }
    //            else if (j > n - 1)
    //            {
    //                j--;
    //                i++;
    //            }
    //            else if (i < 0)
    //            {
    //                i++;
    //                j++;
    //            }
    //            else if (j < 0)
    //            {
    //                j++;
    //                i--;
    //            }
    //            else if (result.Contains(matrix[i][j]))
    //            {
    //                if (direction == "right" || direction == "up")
    //                {
    //                    j++;
    //                    i--;
    //                }
    //                else if (direction == "left" || direction == "down")
    //                {
    //                    j--;
    //                    i++;
    //                }                                              
    //            }
    //            continue;
    //        }

    //        result.Add(matrix[i][j]);

    //        if (direction == "right")
    //        {
    //            j++;                    
    //        }
    //        else if (direction == "left")
    //        {
    //            j--;                    
    //        }
    //        else if (direction == "down")
    //        {
    //            i++;                    
    //        }
    //        else if (direction == "up")
    //        {
    //            i--;                    
    //        }
    //    }

    //    return result;
    //}

    //private static string DetermineDirection(string direction)
    //{
    //    return direction switch
    //    {
    //        "right" => "down",
    //        "down" => "left",
    //        "left" => "up",
    //        "up" => "right",
    //        _ => direction,
    //    };
    //}
}
```

![Spiral Matrix](https://github.com/user-attachments/assets/960278bc-f4a5-443c-921b-5eba377c774b)