# 4 kyu

## Adding Big Numbers

https://www.codewars.com/kata/525f4206b73515bffb000b21/csharp

## Решение 

```C#
using System;

public class Kata
{
    public static string Add(string a, string b)
    {
        string res = "";
        int answer = 0;
        // Преобразуем строки a и b в массивы символов, переворачиваем их
        char[] aArr = a.ToCharArray();
        char[] bArr = b.ToCharArray();
        Array.Reverse(aArr);
        Array.Reverse(bArr);
        // Итерируемся по каждой цифре в a, b или если в answer уже есть цифра
        for (int i = 0; i < aArr.Length || i < bArr.Length || answer != 0; i++)
        {
            // Получаем цифры из a и b, используя метод Char.GetNumericValue
            // Если длина aArr или bArr меньше, чем i, то возвращаем 0
            int aNum = i < aArr.Length ? (int)Char.GetNumericValue(aArr[i]) : 0;
            int bNum = i < bArr.Length ? (int)Char.GetNumericValue(bArr[i]) : 0;
            answer += aNum + bNum;
             // Добавляем последнюю цифру результата в начало строки res
            res = (answer % 10) + res;
            // Обновляем answer на целочисленное деление от ответа на 10
            answer = answer / 10;
        }
        return res;
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    string result1 = Kata.Add("91", "19");
    Console.WriteLine(result1); // 110

    string result2 = Kata.Add("123456789", "987654322");
    Console.WriteLine(result2); // 1111111111

    string result3 = Kata.Add("999999999", "1");
    Console.WriteLine(result3); // 1000000000
}
```