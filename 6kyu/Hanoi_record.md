# 6 kyu

## Hanoi record

https://www.codewars.com/kata/534eb5ad704a49dcfa000ba6/csharp

## Решение 

```C#
using System.Collections.Generic;

static class Kata
{
    // Создание словаря, в котором будут храниться значения количества ходов для каждого количества дисков
    private static readonly Dictionary<int, int> cache = new Dictionary<int, int>();
    public static int Hanoi(int disks)
    {
        if (disks == 0)
            return 0;
        // Если для данного количества дисков уже посчитано количество ходов, возвращаем его из кэша
        // Иначе вычисляем количество ходов для данного количества дисков
        return cache.TryGetValue(disks, out int moves) ? moves : cache[disks] = 2 * Hanoi(disks - 1) + 1;
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    int disks = 5;
    int moves = Kata.Hanoi(disks);
    Console.WriteLine($"Количество ходов для {disks} дисков равно {moves}");
}
```
