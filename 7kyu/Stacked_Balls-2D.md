# 7 kyu

## Stacked Balls - 2D

https://www.codewars.com/kata/5bb804397274c772b40000ca/cpp

## Решение 

```C++
#include <cmath>

double stack_height_2d(int layers)
{
    return layers < 1 ? 0 : std::sqrt(3) / 2 * (layers - 1) + 1;
}
```
## Пример использования 

```C++
#include <iostream>

int main()
{
    int layers = 3;
    double height = stack_height_2d(layers);
    std::cout << "Height of " << layers << " layers: " << height << std::endl; // Height of 3 layers: 2.59808

    return 0;
}
```