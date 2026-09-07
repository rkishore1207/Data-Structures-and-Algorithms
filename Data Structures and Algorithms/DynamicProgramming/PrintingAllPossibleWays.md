# Printing All Possible Ways

```C#
internal class Program
{
    static void Main(string[] args)
    {
        List<List<int>> ways = [[0, 0, 0], [0, 0 ,0]];
        int m = ways.Count;
        int n = ways[0].Count;
        PrintingAllPossibleWays(0, 0, m, n, new Stack<string>());
    }

    public static void PrintingAllPossibleWays(int i, int j, int m, int n, Stack<string> possibleWays)
    {
        if (i > m || j > n)
            return;

        if (i == m - 1 && j == n - 1)
        {
            foreach (string s in possibleWays)
                Console.Write(s + " ");
            Console.WriteLine();
        }

        possibleWays.Push("Down");
        PrintingAllPossibleWays(i + 1, j, m, n, possibleWays);
        possibleWays.Pop();

        possibleWays.Push("Right");
        PrintingAllPossibleWays(i, j + 1, m, n, possibleWays);
        possibleWays.Pop();
    }
}
```
