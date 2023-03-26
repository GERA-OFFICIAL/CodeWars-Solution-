# 8 kyu

## Counting sheep...

https://www.codewars.com/kata/54edbc7200b811e956000556/csharp

## Решение 

```C#
using System;

public static class Kata
{
    public static int CountSheeps(bool[] sheeps)
    {
        // Используя метод FindAll класса Array, находим все элементы массива sheeps, 
        // которые равны true, и возвращаем их количество
        int count = Array.FindAll(sheeps, x => x == true).Length;
        return count;
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    bool[] sheeps = new bool[] { true, false, true, false, true };
    Console.WriteLine(Kata.CountSheeps(sheeps));
}
```