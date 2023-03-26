# 4 kyu

## Sum Strings as Numbers

https://www.codewars.com/kata/5324945e2ece5e1f32000370/cpp

## Решение 

```C++
#include <string>

using namespace std;

string sum_strings(const string& a, const string& b)
{
    string result;
    // carry - переменная для хранения "остатка", n - длина наибольшей строки
    int carry = 0, n = max(a.size(), b.size());
    // задаем емкость для результата, 
    // равную длине наибольшей строки + 1 для возможного переноса
    result.reserve(n + 1);
    // проходимся по символам строк a и b, начиная с конца, 
    // складывая соответствующие символы и прибавляя "остаток" от предыдущего сложения
    for (int i = 0; i < n; i++)
    {
        // если индекс i меньше длины строки a, 
        // добавляем к "остатку" значение символа из строки a
        if (i < a.size()) carry += a[a.size() - 1 - i] - '0';
        // если индекс i меньше длины строки b, 
        // добавляем к "остатку" значение символа из строки b
        if (i < b.size()) carry += b[b.size() - 1 - i] - '0';
        // добавляем к результату символ, равный последней цифре "остатка"
        result.insert(result.begin(), '0' + carry % 10);
        carry /= 10;
    }
    if (carry > 0)
        result.insert(result.begin(), '0' + carry);

    return result.empty() ? "0" : result;
}
```
## Пример использования 

```C++
int main(){
    string a = "123";
    string b = "456";
    string result = sum_strings(a, b);
    cout << a << " + " << b << " = " << result << endl; // 123 + 456 = 579

    return 0;
}
```