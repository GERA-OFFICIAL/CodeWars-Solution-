# 6 kyu

## Count characters in your string

https://www.codewars.com/kata/52efefcbcdf57161d4000091/csharp

## Решение 

```C#
using System;
using System.Collections.Generic;

public class Kata
{
    public static Dictionary<char, int> Count(string str)
    {
        if (string.IsNullOrEmpty(str))
            return new Dictionary<char, int>();
        // Создаём новый словарь для хранения количества вхождений символов
        var charCounts = new Dictionary<char, int>();
        // Преобразуем строку в ReadOnlySpan<char> для повышения производительности
        ReadOnlySpan<char> span = str.AsSpan();

        for (int i = 0; i < span.Length; i++)
        {
            // Если символ ещё не встречался, 
            // добавляем его в словарь с начальным значением 1
            if (!charCounts.ContainsKey(span[i]))
                charCounts[span[i]] = 1;
            // Если символ уже встречался, 
            // увеличиваем счётчик его вхождений на 1
            else
                charCounts[span[i]]++;
        }

        return charCounts;
    }
}
```
## Пример использования 

```C#
static void Main()
{
    string input = "aaaa";
    Dictionary<char, int> charCounts = Kata.Count(input);

    Console.WriteLine("Input: " + input);
    Console.WriteLine("Character Counts:");
    foreach (KeyValuePair<char, int> entry in charCounts)
        Console.WriteLine("{0}: {1}", entry.Key, entry.Value);
}
```
