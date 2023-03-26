# 8 kyu

## Convert a Boolean to a String

https://www.codewars.com/kata/551b4501ac0447318f0009cd/csharp

## Решение 

```C#
using System;

public class kata
{
    public static string BooleanToString(bool b)
    {
        return b.ToString();
    }
}
```
## Пример использования 

```C#
using System;

static void Main(string[] args)
{
    bool b1 = true;
    bool b2 = false;

    Console.WriteLine(kata.BooleanToString(b1));
    Console.WriteLine(kata.BooleanToString(b2));
}
```