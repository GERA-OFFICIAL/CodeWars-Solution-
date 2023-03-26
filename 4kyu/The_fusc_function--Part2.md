# 4 kyu

## The fusc function -- Part 2

https://www.codewars.com/kata/57040e445a726387a1001cf7/csharp

## Решение 

```C#
using System;
using System.Numerics;

public class FuscSolution
{
    public static BigInteger Fusc(BigInteger n)
    {
        BigInteger chet = 1;
        BigInteger nechet = 0;
        if (n == 0)
        {
            return 0;
        }
        while (n > 0)
        {
            if (n % 2 == 1 )
            {
                nechet = chet + nechet;
            }
            else
            {
                chet = chet + nechet;         
            }
          n /= 2;
        }
        return nechet;
    }
}
```
## Пример использования 

```C#
public static void Main()
{
    Console.WriteLine(FuscSolution.Fusc(BigInteger.Zero)); // 0
    Console.WriteLine(FuscSolution.Fusc(BigInteger.One)); // 1
    Console.WriteLine(FuscSolution.Fusc(5)); // 3
    Console.WriteLine(FuscSolution.Fusc(21)); // 8
    Console.WriteLine(FuscSolution.Fusc(9007199254740991L)); // 53
}
```