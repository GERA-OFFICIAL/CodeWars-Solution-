# 6 kyu

## Decode the Morse code

https://www.codewars.com/kata/54b724efac3d5402db00065e/csharp

## Решение 

```C#
using System.Text.RegularExpressions;
using System.Text;

class MorseCodeDecoder
{
    public static string Decode(string morseCode)
    {
        string[] words = Regex.Split(morseCode.Trim(), @"\s{3}");
        StringBuilder result = new StringBuilder();

        foreach (string word in words)
        {
            string[] letters = word.Split(' ');
            foreach (string letter in letters)
            {
                result.Append(MorseCode.Get(letter));
            }
            result.Append(" ");
        }

        return result.ToString().Trim();
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    string input = ".... . -.--   .--- ..- -.. .";
    string expected = "HEY JUDE";

    string actual = MorseCodeDecoder.Decode(input);

    Console.WriteLine("Input: " + input);
    Console.WriteLine("Expected: " + expected); // HEY JUDE
    Console.WriteLine("Actual: " + actual); // HEY JUDE
    Console.WriteLine("Result: " + (expected == actual ? "PASS" : "FAIL")); // PASS
}
```
