# 8 kyu

## Geometry Basics: Distance between points in 2D

https://www.codewars.com/kata/58dced7b702b805b200000be/cpp

## Решение 

```C++
#include <cmath>

double distance_between_two_points(const Point& a, const Point& b) {
    double dx = a.x - b.x;
    double dy = a.y - b.y;
    return std::sqrt(dx * dx + dy * dy);
}
```
## Пример использования 

```C++
#include <iostream>

int main() {
    Point a{3, 3};
    Point b{3, 3};
    double distance = distance_between_two_points(a, b);
    std::cout << "Distance between points (" << a.x << ", " << a.y << ") and (" << b.x << ", " << b.y << ") is " << distance << std::endl;
    a = {5, 1};
    b = {1, 4};
    distance = distance_between_two_points(a, b);
    std::cout << "Distance between points (" << a.x << ", " << a.y << ") and (" << b.x << ", " << b.y << ") is " << distance << std::endl;

    return 0;
}
```