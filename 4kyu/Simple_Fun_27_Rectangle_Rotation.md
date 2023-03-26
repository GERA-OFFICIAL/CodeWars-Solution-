# 4 kyu

## Simple Fun #27: Rectangle Rotation

https://www.codewars.com/kata/5886e082a836a691340000c3/csharp

## Решение 

```C#
namespace myjinxin
{
    using System;

    public class Kata
    {
        public int RectangleRotation(int a, int b)
        {
            int x = (int)(a / Math.Sqrt(2));
            int y = (int)(b / Math.Sqrt(2));
            return 4 * ((x + 1) / 2) * ((y + 1) / 2) + ((x / 2) * 2 + 1) * ((y / 2) * 2 + 1);
        }
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    Kata kata = new Kata();
            
    int result = kata.RectangleRotation(6, 4);
    Console.WriteLine(result); // 23
}
```