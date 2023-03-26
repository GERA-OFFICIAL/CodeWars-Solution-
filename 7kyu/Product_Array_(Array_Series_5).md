# 7 kyu

## Product Array (Array Series #5)

https://www.codewars.com/kata/5a905c2157c562994900009d/csharp

## Решение 

```C#
class Kata
{
    public static int[] ProductArray(int[] array)
    {
        int[] result = new int[array.Length];
        int totalProduct = 1;

        foreach (int num in array)
            totalProduct *= num;

        for (int i = 0; i < array.Length; i++)
            result[i] = totalProduct / array[i];

        return result;
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    int[][] testData = new int[][] {
        new int[] { 12, 20 },
        new int[] { 3, 27, 4, 2 },
        new int[] { 13, 10, 5, 2, 9 },
        new int[] { 16, 17, 4, 3, 5, 2 }
    };

    int[][] expectedResults = new int[][] {
        new int[] { 20, 12 },
        new int[] { 216, 24, 162, 324 },
        new int[] { 900, 1170, 2340, 5850, 1300 },
        new int[] { 2040, 1920, 8160, 10880, 6528, 16320 }
    };

    for (int i = 0; i < testData.Length; i++)
    {
        int[] result = Kata.ProductArray(testData[i]);

        Console.WriteLine("Test case #{0}:", i + 1);
        Console.WriteLine("Input: {0}", string.Join(" ", testData[i]));
        Console.WriteLine("Expected output: {0}", string.Join(" ", expectedResults[i]));
        Console.WriteLine("Actual output: {0}", string.Join(" ", result));
        Console.WriteLine();
    }
}
```