
# Printing Subarrays
## C Sharp
 

```C#
namespace Printing_Subarrays
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] subArray = { 1, 4, 6, 7, 9, 3 };
            for(int i = 0; i < subArray.Length; i++)
            {
                for (int j = i ; j < subArray.Length; j++)
                {
                    for (int k = i; k <= j ; k++)
                    {
                        Console.Write(subArray[k]);
                    }
                    Console.WriteLine();
                }
            }
        }
    }
}
// Output
//1
//14
//146
//1467
//14679
//146793
//4
//46
//467
//4679
//46793
//6
//67
//679
//6793
//7
//79
//793
//9
//93
//3
```

