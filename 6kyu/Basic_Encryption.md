# 6 kyu

## Basic Encryption

https://www.codewars.com/kata/5862fb364f7ab46270000078/csharp

## Решение 

```C#
using System;

public static class Kata
{
    public static string Encrypt(string text, int rule)
    {
        if (string.IsNullOrEmpty(text))
            return string.Empty;

        char[] encryptedChars = new char[text.Length];

        for (int i = 0; i < text.Length; i++)
            encryptedChars[i] = (char)((text[i] + rule) % 256);

        return new string(encryptedChars);
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    Console.WriteLine(Kata.Encrypt("", 1)); // ""
    Console.WriteLine(Kata.Encrypt("a", 1)); // "b"
    Console.WriteLine(Kata.Encrypt("please encrypt me", 2)); // "rngcug\"gpet{rv\"og"
}
```
