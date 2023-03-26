# 6 kyu

## Convert string to camel case

https://www.codewars.com/kata/517abf86da9663f1d2000003/cpp

## Решение 

```C++
#include <string>

using namespace std;

string to_camel_case(string text) {
    if (text.empty()) return text;

    string camelCase = "";
    // Флаг, указывающий на то, является ли первое слово заглавным
    bool isFirstWordCapitalized = isupper(text[0]);

    for (int i = 0; i < text.length(); i++)
    {
        // Если текущий символ является разделителем слов 
        // ('-' или '_'), то пропускаем его
        if (text[i] == '-' || text[i] == '_') {
            i++;
            // Если следующий символ не является концом строки, 
            // то добавляем его в верхнем регистре
            if (i < text.length()) {
                camelCase += toupper(text[i]);
            }
        }
        else 
        {
            // Если текущий символ является первым и первое слово не было заглавным, 
            // то добавляем его в нижнем регистре
            if (i == 0 && !isFirstWordCapitalized) 
                camelCase += tolower(text[i]);
            
            else 
                camelCase += text[i];
        }
    }

    return camelCase;
}
```
## Пример использования 

```C++
#include <iostream>
#include <string>

int main() {
    // Пример использования функции to_camel_case
    string input = "the_stealth_warrior";
    string output = to_camel_case(input);
    cout << "Input: " << input << endl;
    cout << "Output: " << output << endl;//theStealthWarrior

    return 0;
}
```
