# 8 kyu

## Keep Hydrated!

https://www.codewars.com/kata/582cb0224e56e068d800003c/cpp

## Решение 

```C++
#include <cmath>

int litres(double time) {
    return std::floor(time * 0.5);
}
```
## Пример использования 

```C++
int main() {
    cout << "Litres of water consumed: " << litres(2) << endl;
    cout << "Litres of water consumed: " << litres(1.4) << endl;
    cout << "Litres of water consumed: " << litres(12.3) << endl;
    cout << "Litres of water consumed: " << litres(0.82) << endl;
    cout << "Litres of water consumed: " << litres(0) << endl;
    return 0;
}
```