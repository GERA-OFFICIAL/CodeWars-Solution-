# 5 kyu

## Josephus Survivor

https://www.codewars.com/kata/555624b601231dc7a400017a/csharp

## Решение 

```C#
public class JosephusSurvivor
{
    public static int JosSurvivor(int n, int k)
    {
        int res = 0;
        for (int i = 1; i <= n; i++)
        {
            res = (res + k) % i;
        }
        return res + 1;
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    Console.WriteLine(JosephusSurvivor.JosSurvivor(7, 3)); // 4
}
```
