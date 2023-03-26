# 7 kyu

## All Inclusive?

https://www.codewars.com/kata/5700c9acc1555755be00027e/csharp

## Решение 

```C#
using System.Collections.Generic;

public class Rotations
{
    public static bool ContainAllRots(string strng, List<string> arr)
    {
        for (int i = 0; i < strng.Length; i++)
        {
            // Получение новой строки путем циклического сдвига строки strng на i символов
            string rotation = strng.Substring(i) + strng.Substring(0, i);
            // Проверка, содержится ли полученная строка rotation в списке arr
            if (!arr.Contains(rotation))
                return false;
        }
        return true;
    }
}
```
## Пример использования 

```C#
using System;

public static void Main()
{
    List<string> arr = new List<string>(){ "bsjq", "qbsj", "sjqb", "twZNsslC", "jqbs" };
    string strng = "bsjq";
    bool result = Rotations.ContainAllRots(strng, arr);
    Console.WriteLine(result);  // True
}
```