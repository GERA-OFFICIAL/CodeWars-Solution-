# 7 kyu

## Simple remove duplicates

https://www.codewars.com/kata/5ba38ba180824a86850000f7/csharp

## Решение 

```C#
using System.Collections.Generic;

public static class Solution
{
    public static int[] solve(int[] arr)
    {
        // Создаем словарь для хранения последних индексов каждого элемента массива
        Dictionary<int, int> lastIndexes = new Dictionary<int, int>();
        // Создаем список для хранения уникальных элементов в обратном порядке
        List<int> result = new List<int>();

        for (int i = arr.Length - 1; i >= 0; i--)
        {
            // Если текущий элемент еще не был добавлен в словарь, 
            // то добавляем его в список и в словарь
            if (!lastIndexes.ContainsKey(arr[i]))
            {
                result.Add(arr[i]);
                lastIndexes.Add(arr[i], i);
            }
        }
        // Переворачиваем список, чтобы получить 
        // уникальные элементы в правильном порядке
        result.Reverse();
        return result.ToArray();
    }
}
```
## Пример использования 

```C#
static void Main()
    {
        int[] arr = new int[]{3,4,4,3,6,3};
        int[] uniqueArr = Solution.solve(arr);
        
        Console.WriteLine("Исходный массив: [{0}]", string.Join(", ", arr));
        Console.WriteLine("Уникальные элементы: [{0}]", string.Join(", ", uniqueArr)); //[4, 6, 3]
    }
```