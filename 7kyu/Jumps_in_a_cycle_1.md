# 7 kyu

## Jumps in a cycle #1

https://www.codewars.com/kata/63f844fee6be1f0017816ff1/cpp

## Решение 

```C++
#include <vector>
#include <algorithm>

long getJumps(const std::vector<int>& cycle, long long k) {
	// Вычисляем наибольший общий делитель размера цикла и k,
    // используя стандартную функцию std::__gcd из библиотеки алгоритмов C++
    // В результате получаем количество переходов по циклу,
    // необходимых для возврата на начальную позицию после k шагов
	return cycle.size() / std::__gcd(static_cast<long long>(cycle.size()), k);
}
```
## Пример использования 

```C++
int main() {
    std::vector<int> cycle = {1, 5, 7, 8, 9};
    long long k = 2;
    long jumps = getJumps(cycle, k);
    std::cout << "Number of jumps: " << jumps << std::endl;
    
    return 0;
}
```