# 4 kyu

## Explosive Sum

https://www.codewars.com/kata/52ec24228a515e620b0005ef/cpp

## Решение 

```C++
#include<vector>

using ull = unsigned long long;

ull exp_sum(unsigned int n) {
    // Создание вектора ways длиной n + 1 и заполнение его нулями.
    std::vector<ull> ways(n + 1, 0);
    // Изначально у нас только один способ 
    // представить число 0 - не выбирать ни одного числа.
    ways[0] = 1;
    for (unsigned int i = 1; i <= n; i++) {
        // Для каждого числа i перебираем все возможные суммы j от i до n
        for (unsigned int j = i; j <= n; j++) {
            // Для каждой суммы j мы добавляем число способов, которыми мы можем получить эту сумму,
            // используя текущее число i, т.е. мы учитываем все варианты сочетания чисел,
            // которые приводят к сумме j
            ways[j] += ways[j - i];
        }
    }
    return ways[n];
}
```
## Пример использования 

```C++
int main() {
    std::cout << exp_sum(4) << std::endl; // 5
    std::cout << exp_sum(10) << std::endl; // 42
    return 0;
}
```