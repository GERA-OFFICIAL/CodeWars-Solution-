# 8 kyu

## Remove String Spaces

https://www.codewars.com/kata/57eae20f5500ad98e50002c5/cpp

## Решение 

```C++
#include <string>
#include <algorithm>

std::string no_space(const std::string& x)
{
    // Создание новой строки "result" той же длины, что и строка "x", и заполнение ее пробелами
    std::string result(x.size(), ' ');
    // Копирование всех символов из строки "x", которые не являются пробелами, в строку "result"
    // и сохранение итератора, указывающего на элемент за последним скопированным элементом, в "it"
    auto it = std::copy_if(x.begin(), x.end(), result.begin(), [](char c) { return c != ' '; });
    // Изменение размера строки "result" до количества скопированных символов
    result.resize(std::distance(result.begin(), it));
    return result;
}
```
## Пример использования 

```C++
int main()
{
    std::string input = "8 j 8   mBliB8g  imjB8B8  jl  B";
    std::string output = no_space(input);
    std::cout << "Input string: " << input << std::endl;
    std::cout << "Output string: " << output << std::endl;
    return 0;
}
```