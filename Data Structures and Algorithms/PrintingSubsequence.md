# Subsequence in Recursion

`Problem:` Printing all the possible subsequence from this list - [3, 1, 2]

- [], [3], [1], [2], [3,1], [1,2], [3,2], [3,1,2]

```C#
internal class Program
{
    static void Main(string[] args)
    {
        int[] numbers = { 3, 1, 2 };
        Subsequence(0, new List<int>(), numbers);
    }

    private static void Subsequence(int i, List<int> subsequences, int[] numbers)
    {
        if (i >= numbers.Length)
        {
            foreach (var sequence in subsequences)
                Console.Write(sequence + " ");
            Console.WriteLine();
            return;
        }

        subsequences.Add(numbers[i]);
        Subsequence(i + 1, subsequences, numbers);
        subsequences.Remove(numbers[i]);
        Subsequence(i + 1, subsequences, numbers);
    }
}
```

![Subsequence](https://github.com/user-attachments/assets/b1e75d16-9b4e-4cea-9745-67dcda7d494c)

![Subsequence Recursion Tree](https://github.com/user-attachments/assets/14e273a4-6349-4d80-9833-84de6f97007b)
