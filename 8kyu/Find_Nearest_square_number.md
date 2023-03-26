# 8 kyu

## Find Nearest square number

https://www.codewars.com/kata/5a805d8cafa10f8b930005ba/csharp

## Решение 

```C#
using System;

public static class Kata
{
    public static int NearestSq(int n)
    {
        if (n == 0)
            return 0;

        int root = (int)Math.Sqrt(n);
        if (root * root == n)
            return n;

        int lower = root * root;
        int upper = (root + 1) * (root + 1);
        return (n - lower < upper - n) ? lower : upper;
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    Console.Write("Введите число: ");
    int n = int.Parse(Console.ReadLine());
    int nearestSq = Kata.NearestSq(n);
    Console.WriteLine("Ближайшее квадратное число: " + nearestSq);
}
```