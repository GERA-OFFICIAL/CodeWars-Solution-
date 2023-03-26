# 7 kyu

## Decimal Time Conversion

https://www.codewars.com/kata/6397b0d461067e0030d1315e/cpp

## Решение 

```C++
#include <iostream>
#include <sstream>
#include <iomanip>
#include <cmath>

double toIndustrial(int time) {
    return std::round((double)time / 60.0 * 100.0) / 100.0;
}

double toIndustrial(std::string time) {
    // Создаем объект istringstream, который будет использоваться для разбора строки
    std::istringstream iss(time);
    double hours = 0.0, minutes = 0.0;
    char delim = ':';
    // Пытаемся разобрать строку и извлечь часы и минуты
    if (iss >> hours >> delim >> minutes) 
        return std::round((hours + (minutes / 60.0)) * 100.0) / 100.0;
    
    else {
        throw std::invalid_argument("Invalid time string format");
    }
}

std::string toNormal(double time) {
    int hours = (int)time;
    // Извлекаем дробную часть времени, которая соответствует минутам, 
    // и округляем ее до ближайшей минуты
    int minutes = (int)std::round((time - hours) * 100.0 * 60.0 / 100.0);
    // Если количество минут равно 60, 
    // увеличиваем количество часов на 1 и обнуляем количество минут
    if (minutes == 60) {
        hours++;
        minutes = 0;
    }
    std::ostringstream oss;
    oss << hours << ":" << std::setw(2) << std::setfill('0') << minutes;
    return oss.str();
}
```
## Пример использования 

```C++
#include <iostream>

int main() {
    // Пример использования функции toIndustrial с целочисленными значениями
    std::cout << toIndustrial(1) << std::endl; // 0.02
    std::cout << toIndustrial(2) << std::endl; // 0.03
    std::cout << toIndustrial(105) << std::endl; // 1.75

    // Пример использования функции toIndustrial со строками времени
    std::cout << toIndustrial("0:03") << std::endl; // 0.05
    std::cout << toIndustrial("0:04") << std::endl; // 0.07
    std::cout << toIndustrial("1:45") << std::endl; // 1.75

    // Пример использования функции toNormal с дробными значениями времени
    std::cout << toNormal(1.75) << std::endl; // 1:45
    std::cout << toNormal(0.33) << std::endl; // 0:20

    return 0;
}
```