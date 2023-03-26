# 6 kyu

## Thue-Morse Sequence

https://www.codewars.com/kata/591aa1752afcb02fa300002a/csharp

## Решение 

```C#
public class Kata
{
    public static string ThueMorse(int n)
    {
        var sequence = new char[n];
        sequence[0] = '0';

        for (int i = 1; i < n; i *= 2)
        {
            for (int j = 0; j < i && i + j < n; j++)
            {
                sequence[i + j] = (sequence[j] == '0') ? '1' : '0';
            }
        }

        return new string(sequence);
    }
}
```
## Пример использования 

```C#
public static void Main()
{
    string result = Kata.ThueMorse(5);
    Console.WriteLine(result); // 01101
}
```

