# 8 kyu

## Grasshopper - Summation

https://www.codewars.com/kata/55d24f55d7dd296eb9000030/csharp

## Решение 

```C#
using System;

public static class Kata
{
    public static int summation(int num) => num * (num + 1) / 2;
}
```
## Пример использования 

```C#
public static void Main(string[] args)
{
    int result = Kata.summation(8);
    Console.WriteLine($"Суммирование чисел от 1 до 8: {result}");
}
```