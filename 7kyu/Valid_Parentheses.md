# 7 kyu

## Valid Parentheses

https://www.codewars.com/kata/6411b91a5e71b915d237332d/cpp

## Решение 

```C++
#include <string>

bool validParentheses(const std::string& str) {
    int count = 0;
    for (char c : str) {
        if (c == '(') count++;
        else if (c == ')') count--;
        if (count < 0) return false;
    }
    return count == 0;
}
```
## Пример использования 

```C++
#include <iostream>
#include <string>

int main() {
    std::string input = "()";
    bool result = validParentheses(input);
    std::cout << "Input string: " << input << std::endl;
    std::cout << "Expected result: " << true << std::endl;
    std::cout << "Actual result: " << result << std::endl;
    return 0;
}
```