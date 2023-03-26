# 5 kyu

## Weight for weight

https://www.codewars.com/kata/55c6126177c9441a570000cc/csharp

## Решение 

```C#
using System;
using System.Linq;

public class WeightSort
{
    public static string orderWeight(string s)
    {
        if (string.IsNullOrWhiteSpace(s))
            return "";
        // разделить строку на массив строк по пробелам и отсортировать его по весу
        // каждой строки (сумме цифр в строке)
        // затем отсортировать по самой строке
        var weights = s.Split(' ').OrderBy(w => w.Sum(c => c - '0')).ThenBy(w => w);
        return string.Join(" ", weights);
    }
}
```
## Пример использования 

```C#
static void Main() {
    string input = "103 123 4444 99 2000";
    string result = WeightSort.orderWeight(input);
    Console.WriteLine(result); // "2000 103 123 4444 99"
}
```
