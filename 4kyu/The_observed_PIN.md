# 4 kyu

## The observed PIN

https://www.codewars.com/kata/5263c6999e0f40dee200059d/cpp

## Решение 

```C++
#include <string>
#include <vector>
#include <unordered_map>

// хэш-таблица, используется для хранения связи между
// каждой цифрой и списком соседних цифр.
std::unordered_map<char, std::vector<char>> adjacentDigits = {
    {'0', {'0', '8'}},
    {'1', {'1', '2', '4'}},
    {'2', {'1', '2', '3', '5'}},
    {'3', {'2', '3', '6'}},
    {'4', {'1', '4', '5', '7'}},
    {'5', {'2', '4', '5', '6', '8'}},
    {'6', {'3', '5', '6', '9'}},
    {'7', {'4', '7', '8'}},
    {'8', {'0', '5', '7', '8', '9'}},
    {'9', {'6', '8', '9'}}
};

void generatePins(std::string&& current, const std::string& observed, std::string::const_iterator index, std::vector<std::string>&& result) {
    // Если текущий индекс достиг конца наблюдаемой строки, значит мы нашли новый комбинацию PIN-кода, 
    // которую мы добавляем в результаты и выходим из функции.
    if (index == observed.end()) {
        result.push_back(std::move(current));
        return;
    }
    // Для каждой цифры в списке соседних цифр текущего индекса, мы рекурсивно вызываем generatePins,
    // передавая новый код с добавленной текущей цифрой, наблюдаемую строку и увеличенный индекс, 
    // а также список результатов.
    for (char c : adjacentDigits[*index]) {
        generatePins(current + c, observed, index + 1, std::move(result));
    }
}

std::vector<std::string> get_pins(std::string observed) {
    std::vector<std::string> result;
    // Вызываем generatePins, передавая пустой код, наблюдаемую строку, начальный индекс и пустой список результатов.
    generatePins("", observed, observed.begin(), std::move(result));
    return result;
}
```
## Пример использования 

```C++
int main()
{
    std::string observed = "8";
    std::vector<std::string> output = get_pins(observed);
    std::sort(output.begin(), output.end());
    std::cout << "PIN-коды для цифры " << observed << ":\n";
    for (const std::string& pin : output) {
        std::cout << pin << '\n';
    }
    return 0;
}
```