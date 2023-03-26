# 8 kyu

## Third Angle of a Triangle

https://www.codewars.com/kata/5a023c426975981341000014/cpp

## Решение 

```C++
class Triangle {
public:
    static int otherAngle(int a, int b) {
        return 180 - a - b;
    }
};
```
## Пример использования 

```C++
#include <iostream>

int main()
{
    cout << Triangle::otherAngle(30, 60) << endl; // 90
    cout << Triangle::otherAngle(60, 60) << endl; // 60
    cout << Triangle::otherAngle(43, 78) << endl; // 59
    
    return 0;
}
```