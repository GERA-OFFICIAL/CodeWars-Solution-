# 5 kyu

## The Bee

https://www.codewars.com/kata/6408ba54babb196a61d66a65/csharp

## Решение 

```C#
using System;
using System.Numerics;

class Kata
{
    public static BigInteger TheBee(int N)
    {
        int m, i, j;
        // определяем размер матрицы
        m = 2 * N - 1;
        // создаем матрицу для хранения количества путей
        BigInteger[,] fields = new BigInteger[m, m];
        // заполняем матрицу нулями
        for (i = 0; i < m; i++)
        {
            for (j = 0; j < m; j++)
            {
                fields[i, j] = 0;
            }
        }
        // заполняем начальные точки матрицы единицами
        for (i = 0; i < N; i++)
        {
            fields[i, 0] = fields[0, i] = 1;
        }
        // заполняем остальную часть матрицы
        for (i = 1; i < m; i++)
        {
            for (j = 1; j < m; j++)
            {
                // если точка находится внутри сетки
                if (N > Math.Abs(i - j))
                {
                    // вычисляем количество путей до этой точки с помощью формулы рекуррентного соотношения
                    fields[i, j] = fields[i - 1, j] + fields[i, j - 1] + fields[i - 1, j - 1];
                }
            }
        }
        return fields[m - 1, m - 1];
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    var result = Kata.TheBee(2);
    Console.WriteLine(result); // 11
}
```
