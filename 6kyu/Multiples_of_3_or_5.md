# 6 kyu

## Multiples of 3 or 5

https://www.codewars.com/kata/514b92a657cdc65150000006/csharp

## Решение 

```C#
public static class Kata
{
    public static int Solution(int value)
    {
        if (value <= 0) return 0;
        int total = 0;
        for (int i = 1; i < value; i++)
        {
            if (i % 3 == 0 || i % 5 == 0)
            {
                total += i;
            }
        }
        return total;
    }
}
```
## Пример использования 

```C#
public static void Main()
{
    int result = Kata.Solution(10);
    Console.WriteLine(result); // 23
}
```

