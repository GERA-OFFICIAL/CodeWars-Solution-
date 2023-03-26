# 7 kyu

## Fix string case

https://www.codewars.com/kata/5b180e9fedaa564a7000009a/csharp

## Решение 

```C#
class Kata
{
    public static string Solve(string s)
    {
        int countUpper = 0;
        int countLower = 0;
        foreach (char c in s)
        {
            if (char.IsUpper(c))
                countUpper++;

            else if (char.IsLower(c))
                countLower++;
        }
        if (countUpper > countLower)
            return s.ToUpper();

        else
            return s.ToLower();
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    string input = "CODe";
    string result = Kata.Solve(input);
    Console.WriteLine(result); // CODE
}
```