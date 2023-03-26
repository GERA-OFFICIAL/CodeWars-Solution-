# 6 kyu

## Crack the PIN

https://www.codewars.com/kata/5efae11e2d12df00331f91a6/cpp

## Решение 

```C++
#include <cstring>
#include <iomanip>
#include <sstream>
#include <openssl/md5.h>// Заголовочный файл для работы с функцией хеширования MD5

std::string crack(const std::string& hash) {
    // Объявляем массив байтов длиной 16 байт для хранения хеш-кода
    unsigned char md5_digest[MD5_DIGEST_LENGTH];
    // Пробуем подобрать пятизначное число
    for (int i = 0; i < 100000; i++) {
        // Преобразуем число в строку
        std::string str = std::to_string(i);
        // Если строка меньше 5 символов, 
        // дополняем её нулями до 5 символов
        if (str.length() < 5) 
            str = std::string(5 - str.length(), '0') + str;
        // Вычисляем хеш-код MD5 от строки
        MD5(reinterpret_cast<const unsigned char*>(str.c_str()), str.length(), md5_digest);
        // Создаём поток данных для форматированного вывода хеш-кода
        std::ostringstream md5_ss;
        // Устанавливаем формат вывода
        md5_ss << std::hex << std::setfill('0');
        // Преобразуем хеш-код из массива байтов в шестнадцатеричную строку 
        // и записываем в поток данных
        for (unsigned char c : md5_digest) 
            md5_ss << std::setw(2) << static_cast<int>(c);
        

        if (md5_ss.str() == hash) 
            return str;
    }

    return "";
}
```
## Пример использования 

```C++
int main() {
    // Хешированный пин-код
    std::string hash = "827ccb0eea8a706c4c34a16891f84e7b";
    // Попытка подобрать пин-код для хеша
    std::string pin = crack(hash);
    // Вывод найденного пин-кода
    std::cout << "Found pin: " << pin << std::endl;

    return 0;
}
```
