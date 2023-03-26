# 8 kyu

## All Star Code Challenge #18

https://www.codewars.com/kata/5865918c6b569962950002a1

## Решение 

```C#
using System.Linq;
class Kata
{
    public static int StrCount(string str, char letter)
    {
        // Преобразование строки str в массив символов и подсчет количества символов letter
        // с помощью метода Count() и лямбда-выражения
        return str.ToCharArray().Count(c => c == letter);
    }
}
```
## Пример использования 

```C#
using System;
class Program
{
    static void Main(string[] args)
    {
        string str = "Hello World!";
        char letter = 'o';
        int count = Kata.StrCount(str, letter);
        Console.WriteLine($"Количество символов '{letter}' в строке '{str}': {count}");
    }
}
```