# 5 kyu

## Moving Zeros To The End

https://www.codewars.com/kata/52597aa56021e91c93000cb0/csharp

## Решение 

```C#
public class Kata
{
    public static int[] MoveZeroes(int[] arr)
    {
        int i = 0;
        for (int j = 0; j < arr.Length; j++)
        {
            if (arr[j] != 0)
            {
                int temp = arr[i];
                arr[i++] = arr[j];
                arr[j] = temp;
            }
        }
        return arr;
    }
}
```
## Пример использования 

```C#
public static void Main(string[] args)
{
    int[] arr = {1, 2, 0, 1, 0, 1, 0, 3, 0, 1};
    int[] result = Kata.MoveZeroes(arr);
    Console.WriteLine(string.Join(",", result)); // "1,2,1,1,3,1,0,0,0,0"
}
```
