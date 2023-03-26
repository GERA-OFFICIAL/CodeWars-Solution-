# 7 kyu

## The 'spiraling' box

https://www.codewars.com/kata/63b84f54693cb10065687ae5/csharp

## Решение 

```C#
using System;

public class SpiralingBox
{
    public static int[,] CreateBox(int width, int length)
    {
        int[,] grid = new int[length, width];
        for (int i = 0; i < length; i++)
        {
            for (int j = 0; j < width; j++)
            {
                if (i == 0 || j == 0 || i == length - 1 || j == width - 1)
                    grid[i, j] = 1;

                else if (i == 1 || j == 1 || i == length - 2 || j == width - 2)
                    grid[i, j] = 2;

                else
                {
                    int d = Math.Min(i, length - i - 1);
                    int e = Math.Min(j, width - j - 1);
                    grid[i, j] = d < e ? d + 1 : e + 1;
                }
            }
        }
        return grid;
    }
}
```
## Пример использования 

```C#
public static void Main()
{
    int[,] box = SpiralingBox.CreateBox(7, 8);

    for (int i = 0; i < 8; i++)
    {
        for (int j = 0; j < 7; j++)
            Console.Write(box[i, j] + " ");

        Console.WriteLine();
    }
}
```