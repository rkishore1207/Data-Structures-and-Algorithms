# Subsequence Patterns

## Printing First Sum Subsequence

```C#
    public static bool PrintFirstSumSubsequence(int index, int[] numbers, List<int> subsequence, int sum)
    {
        if (index >= numbers.Length)
        {
            if (subsequence.Sum() == sum)
            {
                foreach (int i in subsequence)
                    Console.Write(i + " ");
                return true;
            }
            return false;
        }

        subsequence.Add(numbers[index]);
        if (PrintFirstSumSubsequence(index + 1, numbers, subsequence, sum))
            return true;

        subsequence.Remove(numbers[index]);
        if (PrintFirstSumSubsequence(index + 1, numbers, subsequence, sum))
            return true;

        return false;
    }
```

## Counting the No of Subsequence which is equal to the Sum

```C#
    public static int SubsequenceSumCount(int index, int[] numbers, List<int> subsequence, int sum)
    {
        if (index >= numbers.Length)
        {
            if (subsequence.Sum() == sum)
                return 1;
            return 0;
        }

        subsequence.Add(numbers[index]);
        int left = SubsequenceSumCount(index + 1, numbers, subsequence, sum);

        subsequence.Remove(numbers[index]);
        int right = SubsequenceSumCount(index + 1, numbers, subsequence, sum);

        return left + right;
    }
```
