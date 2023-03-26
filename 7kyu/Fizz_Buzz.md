# 7 kyu

## Fizz / Buzz

https://www.codewars.com/kata/51dda84f91f5b5608b0004cc/csharp

## Решение 

```C#
public class Kata
{
    public static int[] Solution(int number)
    {
        int countMultiplesOfThree = (number - 1) / 3;
        int countMultiplesOfFive = (number - 1) / 5;
        int countMultiplesOfFifteen = (number - 1) / 15;

        int countMultiplesOfThreeAndFive = countMultiplesOfFifteen;

        int countMultiplesOfThreeOnly = countMultiplesOfThree - countMultiplesOfThreeAndFive;
        int countMultiplesOfFiveOnly = countMultiplesOfFive - countMultiplesOfThreeAndFive;

        return new[] { countMultiplesOfThreeOnly, countMultiplesOfFiveOnly, countMultiplesOfThreeAndFive };
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    int number = 20;
    int[] result = Kata.Solution(number);
    Console.WriteLine($"For number = {number}:");
    Console.WriteLine($"Multiples of three only: {result[0]}"); // 5
    Console.WriteLine($"Multiples of five only: {result[1]}"); // 2 
    Console.WriteLine($"Multiples of both three and five: {result[2]}"); // 1
}
```