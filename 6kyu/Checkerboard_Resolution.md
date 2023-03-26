# 6 kyu

## Checkerboard Resolution

https://www.codewars.com/kata/60576b180aef19001bce494d/csharp

## Решение 

```C#
using System;
using System.Numerics;

public static class Kata
{
    public static BigInteger CountCheckerBoard(BigInteger w, BigInteger h, BigInteger r)
    {
        // Функция для подсчёта количества кластеров по горизонтали и вертикали
        // Она принимает параметр 'a', который указывает на размер квадратной доски вдоль одной из осей,
        // и вычисляет количество кластеров, которые могут разместиться вдоль этой оси.
        // Кластер занимает расстояние в 2*r между центрами соседних квадратов.
        BigInteger cluster(BigInteger a) => a / (2 * r);
        // Функция для вычисления расстояния до ближайшего квадрата с заданными координатами
        // Она принимает параметры 'a' и 'b', которые указывают на координаты точки на доске,
        // и вычисляет расстояние от этой точки до ближайшего центра квадрата.
        // Это расстояние состоит из двух частей: b*r - расстояние от центра ближайшего кластера до точки
        // и BigInteger.Max(0, a - b * 2 * r - r) - расстояние от точки до центра ближайшего квадрата внутри кластера
        BigInteger delta(BigInteger a, BigInteger b) => b * r + BigInteger.Max(0, a - b * 2 * r - r);
        // Вычисляем количество кластеров и расстояние до ближайшего квадрата на каждой оси
        var dx1 = delta(w, cluster(w));
        var dy2 = delta(h, cluster(h));
        return dx1 * (h - dy2) + (w - dx1) * dy2;
    }
}
```
## Пример использования 

```C#
static void Main(string[] args) {
    var width = new System.Numerics.BigInteger(11);
    var height = new System.Numerics.BigInteger(33);
    var resolution = new System.Numerics.BigInteger(6);
    var result = Kata.CountCheckerBoard(width, height, resolution);
    Console.WriteLine($"Результат: {result}");
}
```
