# 3 kyu

## Rail Fence Cipher: Encoding and Decoding

https://www.codewars.com/kata/58c5577d61aefcf3ff000081/cpp

## Решение 

```C++
#include <string>
#include <vector>

std::string encode_rail_fence_cipher(const std::string& str, int n)
{
    if (n == 1) return str;
    // Создаем вектор строк для хранения символов на каждом уровне
    std::vector<std::string> rows(n);
    int level = 0;
    int step = 1;

    for (char c : str) {
        // Добавляем символ на текущий уровень
        rows[level] += c;
        // Если достигнут верхний уровень, меняем направление на "вниз"
        if (level == 0) step = 1;
        // Если достигнут нижний уровень, меняем направление на "вверх"
        else if (level == n - 1) step = -1;
        // Переходим на следующий уровень в соответствии с направлением
        level += step;
    }
    // Собираем зашифрованную строку из всех уровней
    std::string result;
    for (const auto& row : rows) {
        result += row;
    }

    return result;
}

std::string decode_rail_fence_cipher(const std::string& str, int n)
{
    if (n == 1) return str;
    std::vector<std::string> rows(n);
    // Создаем вектор для хранения длин строк на каждом уровне
    std::vector<int> row_lengths(n);
    int level = 0;
    int step = 1;
    int index = 0;
    // Заполняем вектор строк пустыми символами и считаем длины строк на уровнях
    for (int i = 0; i < str.size(); i++) {
         // Добавляем пустой символ на текущий уровень и увеличиваем длину строки на уровне
        rows[level] += " ";
        row_lengths[level]++;
        if (level == 0) step = 1;
        else if (level == n - 1) step = -1;
        level += step;
    }
    // Заполняем вектор строк зашифрованной строки
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < row_lengths[i]; j++) {
            rows[i][j] = str[index++];
        }
    }
    // Собираем расшифрованную строку из уровней, восстанавливая порядок символов
    std::string result;
    level = 0;
    step = 1;
    std::vector<int> indices(n);

    for (int i = 0; i < str.size(); i++) {
        result += rows[level][indices[level]++];
        if (level == 0) step = 1;
        else if (level == n - 1) step = -1;
        level += step;
    }

    return result;
}
```
## Пример использования 

```C++
int main()
{
    // Пример использования функции encode_rail_fence_cipher
    std::string input_str = "WEAREDISCOVEREDFLEEATONCE";
    int n = 3;
    std::string encoded_str = encode_rail_fence_cipher(input_str, n);
    std::cout << "Encoded string: " << encoded_str << std::endl; // WECRLTEERDSOEEFEAOCAIVDEN

    // Пример использования функции decode_rail_fence_cipher
    std::string decoded_str = decode_rail_fence_cipher(encoded_str, n);
    std::cout << "Decoded string: " << decoded_str << std::endl; // WEAREDISCOVEREDFLEEATONCE

    return 0;
}
```