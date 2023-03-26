# 8 kyu

## Reversed Strings

https://www.codewars.com/kata/5168bb5dfe9a00b126000018/cpp

## Решение 

```C++
#include <string>

using namespace std;

string reverseString(string str)
{
    int n = str.length();
    for (int i = 0, j = n - 1; i < j; i++, j--)
    {
        // Обмен символов на позициях "i" и "j"
        swap(str[i], str[j]);
    }
    return str;
}
```
## Пример использования 

```C++
int main()
{
    string s = "hello world";
    cout << "Original string: " << s << endl;
    s = reverseString(s);
    cout << "Reversed string: " << s << endl;
    return 0;
}
```