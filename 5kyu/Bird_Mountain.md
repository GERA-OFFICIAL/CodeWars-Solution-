# 5 kyu

## Bird Mountain

https://www.codewars.com/kata/5c09ccc9b48e912946000157/cpp

## Решение 

```C++
#include <vector>
#include <string>
#include <algorithm>

int peak_height(std::vector<std::string>& mountain) {
    if (mountain.empty() || mountain[0].empty()) 
        return 0;

    int h = mountain.size();
    int w = mountain[0].length();
    int max = 0;
    // Заменяем каждый символ ^ на 1, а все остальные символы на 0.
    for (int i = 0; i < h; i++) {
        for (int j = 0; j < w; j++) {
            if (mountain[i][j] == '^') {
                mountain[i][j] = '1';
                max = 1;
            }
            else {
                mountain[i][j] = '0';
            }
        }
    }
     // Флаг, который показывает, 
    // изменился ли горный массив на последней итерации цикла.
    bool isTouched = true;
    int offset = 1;
    // Выполняем итерации, 
    // пока на последней итерации горный массив не будет изменен.
    while (isTouched) {
        isTouched = false;
         // Создаем копию текущего горного массива.
        std::vector<std::string> nextMountain = mountain;
        // Проходим по каждому элементу горного массива
        // (исключая крайние строки и столбцы).
        for (int i = offset; i < h - offset; i++) {
            for (int j = offset; j < w - offset; j++) {
                // Если элемент больше 0 и равен соответствующим элементам сверху, снизу, слева и справа, 
                // то увеличиваем значение элемента на 1.
                if (
                    mountain[i][j] > '0' &&
                    mountain[i][j] == mountain[i + 1][j] &&
                    mountain[i][j] == mountain[i - 1][j] &&
                    mountain[i][j] == mountain[i][j + 1] &&
                    mountain[i][j] == mountain[i][j - 1]
                    ) {
                    nextMountain[i][j] += 1;
                    // Обновляем максимальную высоту пика.
                    max = std::max(nextMountain[i][j] - '0', max);
                    isTouched = true;
                }
            }
        }

        offset++;
        mountain = nextMountain;
    }

    return max;
}
```
## Пример использования 

```C++
int main() {
    std::vector<std::string> mountain = {
        "^^^^^^        ",
        " ^^^^^^^^     ",
        "  ^^^^^^^     ",
        "  ^^^^^       ",
        "  ^^^^^^^^^^^ ",
        "  ^^^^^^      ",
        "  ^^^^        "
    };
    int max_peak_height = peak_height(mountain);
    std::cout << "Максимальная высота пика: " << max_peak_height << std::endl; // 3

    return 0;
}
```