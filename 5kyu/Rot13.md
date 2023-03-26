# 5 kyu

## Rot13

https://www.codewars.com/kata/530e15517bc88ac656000716/cpp

## Решение 

```C++
#include <string>

using namespace std;

string rot13(string message)
{
    string result;
    for (char c : message)
    {
        // Если символ является буквой алфавита
        if (isalpha(c))
        {
            // Определяем начальный символ алфавита для данной буквы (заглавная или строчная)
            char base = isupper(c) ? 'A' : 'a';
            // Вычисляем новую букву, используя формулу rot13
            c = base + (c - base + 13) % 26;
        }
        // Добавляем новый символ в результирующую строку
        result.push_back(c);
    }
    return result;
}
```
## Пример использования 

```C++
int main(){
    string message = "Hello, world!";
    string encrypted = rot13(message);
    cout << "Encrypted message: " << encrypted << endl; // Uryyb, jbeyq!
    string decrypted = rot13(encrypted);
    cout << "Decrypted message: " << decrypted << endl;
    return 0;
}
```
