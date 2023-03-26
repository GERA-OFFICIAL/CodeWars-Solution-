# 8 kyu

## Classy Extentions

https://www.codewars.com/kata/55a14aa4817efe41c20000bc/csharp

## Решение 

```C#
public class Cat : Animal
{
    public Cat(string name) : base(name)
    {
    }
    public override string Speak()
    {
        return $"{Name} meows.";
    }
}
```
## Пример использования 

```C#
using System;

static void Main(string[] args)
{
	Cat cat1 = new Cat("Mr Whiskers");
	Console.WriteLine(cat1.Speak()); 
}
```