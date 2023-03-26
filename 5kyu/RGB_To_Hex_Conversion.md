# 5 kyu

## RGB To Hex Conversion

https://www.codewars.com/kata/513e08acc600c94f01000001/cpp

## Решение 

```C++
#include <string>
#include <algorithm>
#include <sstream>
#include <iomanip>

class RGBToHex
{
public:
    static std::string rgb(int r, int g, int b)
    {
        r = std::clamp(r, 0, 255);
        g = std::clamp(g, 0, 255);
        b = std::clamp(b, 0, 255);
        // создание объекта stringstream для форматирования строки
        std::stringstream ss;
        // использование манипуляторов ввода-вывода, устанавливающих формат вывода, 
        // в данном случае шестнадцатеричный формат, прописные буквы и заполнение нулями
        ss << std::hex << std::uppercase << std::setfill('0');
        // использование манипуляторов ввода-вывода, устанавливающих ширину вывода, 
        // и добавление значений r, g и b в объект stringstream
        ss << std::setw(2) << r << std::setw(2) << g << std::setw(2) << b;

        return ss.str();
    }
};
```
## Пример использования 

```C++
int main(){
    std::cout << RGBToHex::rgb(1, 2, 3) << std::endl; // "010203"
    return 0;
}
```
