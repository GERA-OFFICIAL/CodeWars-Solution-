# 7 kyu

## Hands Up

https://www.codewars.com/kata/56d8f14cba01a83cdb0002a2/cpp

## Решение 

```C++
#include <array>

std::array<int, 3> get_positions(int s) {
    return { s % 3, s / 3 % 3, s / 9 % 3 };
}
```
## Пример использования 

```C++
int main() {
    std::array<int, 3> pos1 = get_positions(54);
    std::cout << "Positions of 54: " << pos1[0] << ", " << pos1[1] << ", " << pos1[2] << std::endl;

    std::array<int, 3> pos2 = get_positions(98);
    std::cout << "Positions of 98: " << pos2[0] << ", " << pos2[1] << ", " << pos2[2] << std::endl;

    std::array<int, 3> pos3 = get_positions(3);
    std::cout << "Positions of 3: " << pos3[0] << ", " << pos3[1] << ", " << pos3[2] << std::endl;

    return 0;
}
```