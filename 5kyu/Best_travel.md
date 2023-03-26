# 5 kyu

## Best travel

https://www.codewars.com/kata/55e7280b40e1c4a06d0000aa/csharp

## Решение 

```C#
using System;
using System.Collections.Generic;
using System.Linq;

public static class SumOfK
{
    public static int? chooseBestSum(int t, int k, List<int> ls)
    {
        if (k == 0 || k > ls.Count)
            return null;
        // Вычисляем максимальную сумму из всех возможных комбинаций k элементов из списка ls,
        // где сумма элементов не превышает t.
        int maxSum = ls.Combinations(k).Select(c => c.Sum()).Where(s => s <= t).DefaultIfEmpty(-1).Max();

        if (maxSum == -1)
            return null;

        return maxSum;
    }
    // Создаем расширяющий метод Combinations для типа IEnumerable<int>,
    // который возвращает все возможные комбинации из k элементов.
    private static IEnumerable<List<int>> Combinations(this IEnumerable<int> ls, int k) =>
        // Если k равно 0, возвращаем список, содержащий пустой список.
        k == 0 ? new[] { new List<int>() } :
        // Иначе для каждого элемента e из списка ls (начиная с первого) находим все комбинации
        // из (k - 1) элементов, которые идут после него, и добавляем в начало этого списка элемент e.
        ls.SelectMany((e, i) => ls.Skip(i + 1).Combinations(k - 1).Select(c => (new[] { e }).Concat(c).ToList()));
}
```
## Пример использования 

```C#
public static void Main()
{
    List<int> ts = new List<int> {50, 55, 56, 57, 58};
    int? n = SumOfK.chooseBestSum(163, 3, ts);
    Console.WriteLine(n); // 163
    
    ts = new List<int> {50}; 
    n = SumOfK.chooseBestSum(163, 3, ts);
    Console.WriteLine(n); // пустая строка

    ts = new List<int> {91, 74, 73, 85, 73, 81, 87};
    n = SumOfK.chooseBestSum(230, 3, ts);
    Console.WriteLine(n); // 228
}

```