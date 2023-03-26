# 7 kyu

## Mysterious Singularity Numbers

https://www.codewars.com/kata/6409aa6df4a0b773ce29cc3d/cpp

## Решение 

```C++
unsigned int realNumbers(unsigned int n) {
    return n - (n / 2 + n / 3 + n / 5 - n / 6 - n / 10 - n / 15 + n / 30);
}
```
## Пример использования 

```C++
int main() {
    unsigned int n = 5;
    cout << "For n = " << n << ", real numbers = " << realNumbers(n) << endl;
    n = 10;
    cout << "For n = " << n << ", real numbers = " << realNumbers(n) << endl;
    n = 20;
    cout << "For n = " << n << ", real numbers = " << realNumbers(n) << endl;
    n = 30;
    cout << "For n = " << n << ", real numbers = " << realNumbers(n) << endl;
    n = 40;
    cout << "For n = " << n << ", real numbers = " << realNumbers(n) << endl;
    n = 55;
    cout << "For n = " << n << ", real numbers = " << realNumbers(n) << endl;
    
    return 0;
}
```