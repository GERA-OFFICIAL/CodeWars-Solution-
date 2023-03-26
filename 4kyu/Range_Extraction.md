# 4 kyu

##  Range Extraction

https://www.codewars.com/kata/51ba717bb08c1cd60f00002f/csharp

## Решение 

```C#
using System.Text;

public class RangeExtraction
{
    public static string Extract(int[] args)
    {
        if (args == null || args.Length == 0)
            return "";

        var result = new StringBuilder();
        var start = args[0];
        var last = start;

        for (var i = 1; i < args.Length; i++)
        {
            // Если текущий элемент равен предыдущему плюс один, 
            // значит это продолжение диапазона
            if (args[i] == last + 1)
                last = args[i];

            else
            {
                // Если диапазон состоит из одного элемента, 
                // то добавляем его в результирующую строку через запятую
                if (start == last)
                    result.Append($"{start},");
                // Иначе, если диапазон состоит из двух элементов, 
                // то добавляем их в результирующую строку через запятую
                else if (last == start + 1)
                    result.Append($"{start},{last},");

                else
                    result.Append($"{start}-{last},");
                 // Обновляем переменные start и last для следующего диапазона
                start = args[i];
                last = start;
            }
        }
        // Добавляем последний диапазон в результирующую строку
        if (start == last)
            result.Append($"{start}");

        else if (last == start + 1)
            result.Append($"{start},{last}");

        else
            result.Append($"{start}-{last}");

        return result.ToString();
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    int[] arr = { 1, 2, 3, 4, 6, 7, 8, 10, 11, 12, 14 };
    string result = RangeExtraction.Extract(arr);
    Console.WriteLine(result); // "1-4,6-8,10-12,14"
}
```






