# 8 kyu

## Find out whether the shape is a cube

https://www.codewars.com/kata/58d248c7012397a81800005c/csharp

## Решение 

```C#
namespace CubeCheck
{
    using System;
    public class CubeChecker
    {
        public bool IsCube(double volume, double side)
        {
            // Если объем или сторона куба меньше или равны 0, возвращаем false
            if (volume <= 0 || side <= 0) return false;
            // Рассчитываем сторону куба из объема
            double calculatedSide = Math.Pow(volume, 1.0 / 3.0);
            // Если рассчитанная сторона куба и переданная сторона куба различаются меньше, чем на 1e-10
            // И если рассчитанный объем куба и переданный объем куба различаются меньше, чем на 1e-10,
            // то возвращаем true (куб существует)
            if (Math.Abs(calculatedSide - side) < 1e-10 && Math.Abs(calculatedSide * calculatedSide * calculatedSide - volume) < 1e-10)
            {
                return true;
            }
            else
            {
                return false;
            }
        }
    }
}
```
## Пример использования 

```C#
public static void Main(string[] args)
{
    CubeChecker cube = new CubeChecker();
    bool result1 = cube.IsCube(1, 1); // true
    bool result2 = cube.IsCube(2, 1); // false
    bool result3 = cube.IsCube(6, 3); // false
    bool result4 = cube.IsCube(-8, -2); // false
    bool result5 = cube.IsCube(0, 0); // false
        
    Console.WriteLine(result1);
    Console.WriteLine(result2);
    Console.WriteLine(result3);
    Console.WriteLine(result4);
    Console.WriteLine(result5);
}
```