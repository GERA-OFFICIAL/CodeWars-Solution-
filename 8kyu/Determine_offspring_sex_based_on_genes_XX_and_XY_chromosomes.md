# 8 kyu

## Determine offspring sex based on genes XX and XY chromosomes

https://www.codewars.com/kata/56530b444e831334c0000020/cpp

## Решение 

```C++
std::string chromosomeCheck(std::string sperm) {
    return (sperm == "XY") ? "Congratulations! You're going to have a son." :
        (sperm == "XX") ? "Congratulations! You're going to have a daughter." :
        "Invalid input.";
}
```
## Пример использования 

```C++
#include <iostream>
#include <string>

int main() {
    string sperm1 = "XY";
    string sperm2 = "XX";
    string sperm3 = "YY";

    cout << chromosomeCheck(sperm1) << endl; 
    cout << chromosomeCheck(sperm2) << endl; 
    cout << chromosomeCheck(sperm3) << endl; 

    return 0;
}
```