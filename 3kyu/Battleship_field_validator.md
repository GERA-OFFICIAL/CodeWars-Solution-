# 3 kyu

## Battleship field validator

https://www.codewars.com/kata/52bb6539a4cf1b12d90005b7/csharp

## Решение 

```C#
namespace Solution
{
    public class BattleshipField
    {
        public static bool ValidateBattlefield(int[,] field)
        {
            int sum = 0;
            for (int i = 0; i < field.GetLength(0); i++)
                for (int j = 0; j < field.GetLength(1); j++)
                    sum += field[i, j];
            // Если сумма не равна 20, значит на поле не расставлены 
            // все корабли или их суммарная длина неверна
            if (sum != 20) return false;
            // Проверяем, чтобы корабли не соприкасались углами
            for (int i = 0; i < 9; i++)
                for (int j = 0; j < 9; j++)
                    if ((field[i, j] + field[i + 1, j + 1] == 2) || (field[i + 1, j] + field[i, j + 1] == 2))
                        return false;
            // Проверяем, чтобы каждого размера кораблей было нужное количество
            for (int k = 4; k > 1; k--)
            {
                int ships = 0;
                for (int i = 0; i < 10; i++)
                    for (int j = 0; j < 11 - k; j++)
                    {
                        int s1 = 0, s2 = 0;
                        for (int l = 0; l < k; l++)
                        {
                            s1 += field[i, j + l];
                            s2 += field[j + l, i];
                        }
                        if (s1 == k) ships++;
                        if (s2 == k) ships++;
                    }
                // Формула для вычисления количества кораблей нужного размера
                if (ships != 1 + (3 / k) * 3 + (2 / k) * 6) return false;
            }
            return true;
        }
    }
}
```
## Пример использования 

```C#
using System;

static void Main(string[] args) {
    int[,] field = new int[10,10]
                 {{1, 0, 0, 0, 0, 1, 1, 0, 0, 0},
                  {1, 0, 1, 0, 0, 0, 0, 0, 1, 0},
                  {1, 0, 1, 0, 1, 1, 1, 0, 1, 0},
                  {1, 0, 0, 0, 0, 0, 0, 0, 0, 0},
                  {0, 0, 0, 0, 0, 0, 0, 0, 1, 0},
                  {0, 0, 0, 0, 1, 1, 1, 0, 0, 0},
                  {0, 0, 0, 0, 0, 0, 0, 0, 1, 0},
                  {0, 0, 0, 1, 0, 0, 0, 0, 0, 0},
                  {0, 0, 0, 0, 0, 0, 0, 1, 0, 0},
                  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0}};
    bool isValid = BattleshipField.ValidateBattlefield(field);
    Console.WriteLine("The field is valid: " + isValid); // true
}
```