# 3 kyu

## Make a spiral

https://www.codewars.com/kata/534e01fbbb17187c7e0000c6/csharp

## Решение 

```C#
public class Spiralizor
{
    public static int[,] Spiralize(int size)
    {
        int[,] spiral = new int[size, size];

        for (int i = 0; i < size; i++)
        {
            for (int j = 0; j < size; j++)
                spiral[i, j] = 0;
        }
        // Задаем начальное значение координат row и col и длину стороны side_length.
        int row = 0, col = 0, side_length = size;
        // Для каждой стороны квадрата нарисуем спираль.
        for (; side_length >= 1; row += 2, col += 2, side_length -= 4)
        {
            DrawSpiral(spiral, row, col, side_length);
        }
        return spiral;
    }
    // Функция DrawSpiral рисует спираль на текущей стороне квадрата.
    private static void DrawSpiral(int[,] spiral, int row, int col, int side_length)
    {
        // Рисуем верхнюю, нижнюю, левую и правую стороны квадрата.
        for (int i = 0; i < side_length; i++)
        {
            spiral[row, col + i] = 1;// Верхняя сторона
            spiral[row + side_length - 1, col + i] = 1;// Нижняя сторона
            spiral[row + i, col] = 1;// Левая сторона
            spiral[row + i, col + side_length - 1] = 1;// Правая сторона
        }
        // Делаем дополнительные шаги, чтобы убрать некоторые лишние элементы.
        spiral[row + 1, col] = 0;

        if (side_length > 4)
            spiral[row + 2, col + 1] = 1;
    }
}
```
## Пример использования 

```C#
static void Main(string[] args)
{
    int input = 5;
    int[,] spiral = Spiralizor.Spiralize(input);
    Console.WriteLine("Spiral of size " + input + ":");
    for (int i = 0; i < input; i++)
    {
        for (int j = 0; j < input; j++)
            Console.Write(spiral[i, j] + " ");

        Console.WriteLine();
    }
}
```