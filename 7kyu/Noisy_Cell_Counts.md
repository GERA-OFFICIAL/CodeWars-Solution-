# 7 kyu

## Noisy Cell Counts

https://www.codewars.com/kata/63ebadc7879f2500315fa07e/cpp

## Решение 

```C++
#include <vector>

std::vector<int> cleaned_counts(const std::vector<int>& data) {
    std::vector<int> cleaned_data = { data[0] };
    for (int i = 1; i < data.size(); i++) {
        // Если текущий элемент меньше последнего элемента в cleaned_data,
        // добавляем в конец cleaned_data последний элемент, иначе добавляем
        // текущий элемент.
        if (data[i] < cleaned_data.back()) 
            cleaned_data.push_back(cleaned_data.back());

        else 
            cleaned_data.push_back(data[i]);
    }
    return cleaned_data;
}
```
## Пример использования 

```C++
int main() {
    std::vector<int> data = {2, 1, 1};
    std::vector<int> result = cleaned_counts(data);

    std::cout << "Input data: "; // 2 1 1
    for (const auto& i : data) {
        std::cout << i << " ";
    }

    std::cout << "\nCleaned counts: "; // 2 2 2
    for (const auto& i : result) {
        std::cout << i << " ";
    }
    std::cout << std::endl;

    return 0;
}
```