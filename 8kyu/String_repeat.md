# 8 kyu

## String repeat

https://www.codewars.com/kata/57a0e5c372292dd76d000d7e/csharp

## Решение 

```C#
namespace Solution
{
    public static class Program
    {
        public static string RepeatStr(int n, string s)
        {
            string result = "";
            for (int i = 0; i < n; i++)
                result += s;

            return result;
        }
    }
}
```
## Пример использования 

```C#
using System;

static void Main(string[] args)
{
    string repeatedString = Program.RepeatStr(4, "hello");
    Console.WriteLine(repeatedString); 
}
```