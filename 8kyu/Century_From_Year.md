# 8 kyu

## Century From Year

https://www.codewars.com/kata/5a3fe3dde1ce0e8ed6000097

## Решение 

```C++
int centuryFromYear(int year) {
    return (year + 99) / 100;
}
```
## Пример использования 

```C++
#include <iostream>

int main() {
    std::cout << "The century of the year 1705 is: " << centuryFromYear(1705) << std::endl;
    std::cout << "The century of the year 1900 is: " << centuryFromYear(1900) << std::endl;
    std::cout << "The century of the year 1601 is: " << centuryFromYear(1601) << std::endl;
    std::cout << "The century of the year 2000 is: " << centuryFromYear(2000) << std::endl;
    return 0;
}
```