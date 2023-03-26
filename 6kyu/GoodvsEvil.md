# 6 kyu

## Good vs Evil

https://www.codewars.com/kata/52761ee4cffbc69732000738/csharp

## Решение 

```C#
public class Kata
{
    public static string GoodVsEvil(string good, string evil)
    {
        string[] goodForcesStr = good.Split(' ');
        int[] goodForces = new int[goodForcesStr.Length];

        for (int i = 0; i < goodForcesStr.Length; i++)
            goodForces[i] = int.Parse(goodForcesStr[i]);
        
        string[] evilForcesStr = evil.Split(' ');
        int[] evilForces = new int[evilForcesStr.Length];

        for (int i = 0; i < evilForcesStr.Length; i++)
            evilForces[i] = int.Parse(evilForcesStr[i]);
        

        int goodScore = goodForces[0] * 1 + goodForces[1] * 2 + goodForces[2] * 3 + goodForces[3] * 3 +
            goodForces[4] * 4 + goodForces[5] * 10;
        int evilScore = evilForces[0] * 1 + evilForces[1] * 2 + evilForces[2] * 2 + evilForces[3] * 2 +
            evilForces[4] * 3 + evilForces[5] * 5 + evilForces[6] * 10;

        if (goodScore > evilScore)
            return "Battle Result: Good triumphs over Evil";

        else if (goodScore < evilScore)
            return "Battle Result: Evil eradicates all trace of Good";
        
        else
            return "Battle Result: No victor on this battle field";
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    string result = Kata.GoodVsEvil("1 1 1 1 1 1", "1 1 1 1 1 1 1");
    Console.WriteLine(result); // Battle Result: Evil eradicates all trace of Good
}
```
