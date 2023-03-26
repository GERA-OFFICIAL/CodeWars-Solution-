# 5 kyu

## Simple Pig Latin

https://www.codewars.com/kata/520b9d2ad5c005041100000f/csharp

## Решение 

```C#
using System.Text.RegularExpressions;

public class Kata
{
    public static string PigIt(string str)
    {
        // Разбиваем строку на слова и сохраняем их в массив
        string[] words = str.Split();
        string[] pigWords = new string[words.Length];

        for (int i = 0; i < words.Length; i++)
        {
            string word = words[i];
            // Формируем новое слово в формате "первая буква + остальные буквы + 'ay'"
            string pigWord = $"{word.Substring(1)}{word[0]}";
             // Если слово содержит более одной буквы, добавляем в конец 'ay'
            if (word.Length > 1)
            {
                pigWord += "ay";
            }
            // Добавляем новое "свинское" слово в массив
            pigWords[i] = pigWord;
        }

        return string.Join(" ", pigWords);
    }
}
```
## Пример использования 

```C#
public static void Main()
{
    string input = "Pig latin is cool";
    string output = Kata.PigIt(input);
    Console.WriteLine(output); // "igPay atinlay siay oolcay"
}
```
