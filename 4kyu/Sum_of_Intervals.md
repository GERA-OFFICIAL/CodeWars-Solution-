# 4 kyu

## Sum of Intervals

https://www.codewars.com/kata/52b7ed099cdc285c300001cd/csharp

## Решение 

```C#
using System;
using System.Collections.Generic;

public class Intervals
{
    public static int SumIntervals((int, int)[] intervals)
    {
        if (intervals == null || intervals.Length == 0)
            return 0;
        // Сортировка массива интервалов по начальным значениям (Item1)
        Array.Sort(intervals, (a, b) => a.Item1.CompareTo(b.Item1));
        // Создание списка объединенных интервалов, начальное значение - первый интервал из массива
        var mergedIntervals = new List<(int, int)> { intervals[0] };
        // Объединение пересекающихся интервалов
        for (int i = 1; i < intervals.Length; i++)
        {
            // Если текущий интервал пересекается с последним интервалом из списка, то объединяем их
            if (intervals[i].Item1 <= mergedIntervals[mergedIntervals.Count - 1].Item2)
            {
                var newInterval = (mergedIntervals[mergedIntervals.Count - 1].Item1, Math.Max(mergedIntervals[mergedIntervals.Count - 1].Item2, intervals[i].Item2));
                mergedIntervals[mergedIntervals.Count - 1] = newInterval;
            }
            else
            {
                mergedIntervals.Add(intervals[i]);
            }
        }

        int totalLength = 0;
         // Вычисление общей длины объединенных интервалов
        foreach (var interval in mergedIntervals)
            totalLength += interval.Item2 - interval.Item1;

        return totalLength;
    }
}
```
## Пример использования 

```C#
static void Main()
{
    var intervals = new (int, int)[] { (1, 4), (7, 10), (3, 5) };
    int sum = Intervals.SumIntervals(intervals);
    Console.WriteLine(sum); // 7
}
```