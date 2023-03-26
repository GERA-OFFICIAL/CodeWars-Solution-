# 7 kyu

## Knight vs King

https://www.codewars.com/kata/564e1d90c41a8423230000bc/csharp

## Решение 

```C#
using System;

public class KnightKing
{
    public static string KnightVsKing(object[] knightPosition, object[] kingPosition)
    {
        // Присваиваем переменным x1, y1, x2 и y2 
        // координаты коня и короля из соответствующих массивов
        int x1 = (int)knightPosition[0], y1 = ((string)knightPosition[1])[0];
        int x2 = (int)kingPosition[0], y2 = ((string)kingPosition[1])[0];
        // Вычисляем расстояние между конем и королем
        // как максимум из модулей разности их координат по горизонтали и вертикали
        int distance = Math.Max(Math.Abs(x1 - x2), Math.Abs(y1 - y2));

        if (distance == 1)
        {
            return "King";
        }
        else if (distance == 2)
        {
            return "Knight";
        }
        else
        {
            return "None";
        }
    }
}
```
## Пример использования 

```C#
static void Main(){
    object[] kingPosition = { 4, "C" };
    object[] knightPosition = { 6, "D" };
    string winner = KnightKing.KnightVsKing(knightPosition, kingPosition);
    Console.WriteLine("Winner is: " + winner); // Knight
}
```