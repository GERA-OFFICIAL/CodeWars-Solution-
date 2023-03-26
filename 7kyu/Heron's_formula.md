# 7 kyu

## Heron's formula

https://www.codewars.com/kata/57aa218e72292d98d500240f/csharp

## Решение 

```C#
using System;

namespace Solution
{
    public static class Program
    {
        public static double Heron(double a, double b, double c)
        {
            double s = (a + b + c) / 2;
            double areaSquared = s * (s - a) * (s - b) * (s - c);
            return Math.Sqrt(areaSquared);
        }
    }
}
```
## Пример использования 

```C#
 static void Main() {
    double a = 3.0;
    double b = 4.0;
    double c = 5.0;
    
    double area = Program.Heron(a, b, c);
    
    Console.WriteLine($"Area: {area}");
}
```