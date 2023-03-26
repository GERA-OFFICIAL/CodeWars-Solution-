# 8 kyu

## Count the number of cubes with paint on

https://www.codewars.com/kata/5763bb0af716cad8fb000580/cpp

## Решение 

```C++
int countSquares(int cuts)
{
    if (cuts == 0) {
        return 1;
    }
    int n = cuts + 1;
    return n * n * n - (n - 2) * (n - 2) * (n - 2);
}
```
## Пример использования 

```C++
#include <iostream>

int main() {
    std::cout << countSquares(5) << std::endl;
    std::cout << countSquares(16) << std::endl;
    std::cout << countSquares(23) << std::endl;
    return 0;
}
```