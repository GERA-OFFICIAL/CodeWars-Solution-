# 7 kyu

## Divide and Conquer

https://www.codewars.com/kata/57eaec5608fed543d6000021/csharp

## Решение 

```C#
using System;
using System.Linq;

public class Kata
{
    public static int DivCon(object[] objArray)
    {
        // Используя метод OfType, получаем только те элементы массива, которые являются типом int,
        // и находим их сумму при помощи метода Sum
        int sumOfInts = objArray.OfType<int>().Sum();
        // Используя метод OfType, получаем только те элементы массива, которые являются типом string,
        // и находим их сумму при помощи метода Sum, преобразовав каждый элемент в тип int методом Parse
        int sumOfStrings = objArray.OfType<string>().Sum(str => int.Parse(str));

        return sumOfInts - sumOfStrings;
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    object[] arr = new object[] { 9, 3, "7", "3" };
    int result = Kata.DivCon(arr);
    Console.WriteLine(result); // 2
}
```