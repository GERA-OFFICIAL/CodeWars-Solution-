# 8 kyu

## Is n divisible by x and y?

https://www.codewars.com/kata/5545f109004975ea66000086/cpp

## Решение 

```C++
bool isDivisible(int n, int x, int y) {
    return (n % x == 0) && (n % y == 0);
}
```
## Пример использования 

```C++
#include <iostream>

int main() {
    bool result = isDivisible(3, 3, 4);
    cout << "isDivisible(3, 3, 4) = " << result << endl;
    return 0;
}
```