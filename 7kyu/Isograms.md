# 7 kyu

## Isograms

https://www.codewars.com/kata/54ba84be607a92aa900000f1/cpp

## Решение 

```C++
#include <string>
#include <unordered_set>

bool is_isogram(std::string str) {
    // создаем unordered_set для хранения уникальных символов
    std::unordered_set<char> unique_chars;
    for (char c : str) {
        // если символ уже был добавлен, возвращаем false
        if (unique_chars.count(std::toupper(c)) > 0) {
            return false;
        }
        unique_chars.insert(std::toupper(c));// добавляем символ в unordered_set
    }
    return true;
}
```
## Пример использования 

```C++
int main() {
    assert(is_isogram("Dermatoglyphics") == true);
    assert(is_isogram("moose") == false);
    assert(is_isogram("isIsogram") == false);
    std::cout << "All tests passed." << std::endl;
    
    return 0;
}
```