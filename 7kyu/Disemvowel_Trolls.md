# 7 kyu

## Disemvowel Trolls

https://www.codewars.com/kata/52fba66badcd10859f00097e/csharp

## Решение 

```C#
using System;

public static class Kata
{
    // Создаем статический метод Disemvowel, который принимает строку и возвращает новую строку,
    // из которой удалены все гласные буквы(+ заглавные)(a, e, i, o, u)
    public static string Disemvowel(string str) => string.Join("", Array.FindAll(str.ToCharArray(), c => !"aeiouAEIOU".Contains(c)));
}
```
## Пример использования 

```C#
using System;

public static void Main()
{
    string input = "This website is for losers LOL!";
    string result = Kata.Disemvowel(input);
    Console.WriteLine(result); // Ths wbst s fr lsrs LL!
}
```