# 8 kyu

## Function 1 - hello world

https://www.codewars.com/kata/523b4ff7adca849afe000035/csharp

## Решение 

```C#
using System;

public static class Kata
{
    public static string greet()
    {
        return "hello world!";
    }
}

/*
    Examples:
    
         return @"
          _   _      _ _          __        __         _     _ _ 
         | | | | ___| | | ___     \ \      / /__  _ __| | __| | |
         | |_| |/ _ \ | |/ _ \_____\ \ /\ / / _ \| '__| |/ _` | |
         |  _  |  __/ | | (_) |_____\ V  V / (_) | |  | | (_| |_|
         |_| |_|\___|_|_|\___/       \_/\_/ \___/|_|  |_|\__,_(_)
        ";

        Console.BackgroundColor = ConsoleColor.Blue;
        Console.ForegroundColor = ConsoleColor.White;
        Console.WriteLine(" hello world! ");
        Console.ResetColor();

        return "h\te\tl\tl\to\nw\to\tr\tl\td\t!";

*/
```
## Пример использования 

```C#
static void Main()
{
    Console.BackgroundColor = ConsoleColor.Blue;
    Console.ForegroundColor = ConsoleColor.White;
    Console.WriteLine(" hello world! ");
    Console.ResetColor();
}
```