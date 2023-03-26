# 6 kyu

## Are they the "same"?

https://www.codewars.com/kata/550498447451fbbd7600041c/cpp

## Решение 

```C++
#include <vector>
#include <algorithm>

class Same {
public:
    static bool comp(std::vector<int>& a, std::vector<int>& b) {
        if (a.size() != b.size()) return false;
        // Возводим все элементы вектора 'a' в квадрат
        std::transform(a.begin(), a.end(), a.begin(), [](int i) { return i * i; });
        // Сортируем векторы
        std::sort(a.begin(), a.end());
        std::sort(b.begin(), b.end());
        return std::equal(a.begin(), a.end(), b.begin());
    }
};
```
## Пример использования 

```C++
#include <iostream>
#include <vector>

int main() {
    std::vector<int> a = { 3, 4, 5 };
    std::vector<int> b = { 25, 16, 9 };
    bool result = Same::comp(a, b);
    std::cout << std::boolalpha << result << std::endl; // true

    return 0;
}
```