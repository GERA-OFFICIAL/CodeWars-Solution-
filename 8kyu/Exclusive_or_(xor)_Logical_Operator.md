# 8 kyu

## Exclusive "or" (xor) Logical Operator

https://www.codewars.com/kata/56fa3c5ce4d45d2a52001b3c/csharp

## Решение 

```C#
public class Kata
{
    public static bool Xor(bool a, bool b)
    {
        return (a || b) && !(a && b);
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    bool a = true;
    bool b = false;
    bool result = Kata.Xor(a, b);

    Console.WriteLine($"Результат операции исключающего или между {a} и {b} равен: {result}");
}
```