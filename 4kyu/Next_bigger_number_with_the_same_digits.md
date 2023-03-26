# 4 kyu

## Next bigger number with the same digits

https://www.codewars.com/kata/55983863da40caa2c900004e/cpp

## Решение 

```C++
long nextBigger(long n) {
    // Преобразуем число в строку, чтобы было удобнее работать с его цифрами
    std::string s = std::to_string(n);
    // Находим индекс разрыва(pivot) - последней цифры, которая меньше следующей за ней
    int pivot = -1;
    for (int i = s.size() - 2; i >= 0; i--) {
        if (s[i] < s[i + 1]) {
            pivot = i;
            break;
        }
    }
    // Если разрыв не найден, значит число уже является наибольшим возможным
    if (pivot == -1) 
        return -1;
    // Находим индекс цифры, наименьшей из тех, которые больше разрыва
    int swap = -1;
    for (int i = s.size() - 1; i > pivot; i--) {
        if (s[i] > s[pivot]) {
            swap = i;
            break;
        }
    }
    // Меняем местами разрыв и цифру, которая наименьшая из тех, которые больше разрыва
    std::swap(s[pivot], s[swap]);
    // Разворачиваем подстроку после разрыва, чтобы получить наименьшее возможное число из оставшихся цифр
    std::reverse(s.begin() + pivot + 1, s.end());
    // Преобразуем строку обратно в число
    long result = std::stol(s);

    return result;
}
```
## Пример использования 

```C++
int main() {
    std::cout << nextBigger(12) << std::endl; // 21
    std::cout << nextBigger(513) << std::endl; // 531
    std::cout << nextBigger(2017) << std::endl; // 2071
    std::cout << nextBigger(414) << std::endl; // 441
    std::cout << nextBigger(144) << std::endl; // 414
    std::cout << nextBigger(10990) << std::endl; // 19009

    return 0;
}
```






