# 7 kyu

## String ends with?

https://www.codewars.com/kata/51f2d1cafc9c0f745c00037d/cpp

## Решение 

```C++
#include <string>

bool solution(std::string const& str, std::string const& ending) {
    if (ending.size() > str.size()) 
        return false;
    
    return str.substr(str.size() - ending.size()) == ending;
}
```
## Пример использования 

```C++
#include <iostream>

int main() {
    std::string str = "Hello, world!";
    std::string ending = "world!";
    std::cout << solution(str, ending) << std::endl; // true
    return 0;
}
```