# 4 kyu

## Counting Change Combinations

https://www.codewars.com/kata/541af676b589989aed0009e7/cpp

## Решение 

```C++
#include <vector>
#include <iostream>

unsigned long long countChange(const unsigned int money, const std::vector<unsigned int>& coins) {
    // Создание вектора a с размером, равным сумме денег, и заполнение его нулями.
    std::vector<unsigned long long> a(money + 1);
    // Изначально у нас только один способ 
    // собрать нулевую сумму денег - не выбирать ни одну монету.
    a[0] = 1;
    for (const auto& coin : coins) {
        // Перебираем все возможные суммы денег
        for (unsigned int j = coin; j <= money; j++) {
            // Для каждой суммы денег j мы добавляем число способов, которыми мы можем получить эту сумму,
            // используя текущую монету coin, т.е. мы учитываем все варианты сочетания монет,
            // которые приводят к сумме j
            a[j] += a[j - coin];
        }
    }
    return a[money];
}
```
## Пример использования 

```C++
int main() {
    std::cout << countChange(4, {1, 2}) << std::endl; // 3
    std::cout << countChange(10, {5, 2, 3}) << std::endl; // 4
    return 0;
}
```