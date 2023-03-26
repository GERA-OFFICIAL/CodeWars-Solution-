# 5 kyu

## Directions Reduction

https://www.codewars.com/kata/550f22f4d758534c1100025a/cpp

## Решение 

```C++
#include <string>
#include <vector>
#include <algorithm>

class DirReduction {
public:
    static std::vector<std::string> dirReduc(std::vector<std::string>& arr) {
        std::vector<std::string> result;
        for (const auto& direction : arr) {
            if (!result.empty() &&
                ((result.back() == "NORTH" && direction == "SOUTH") ||
                    (result.back() == "SOUTH" && direction == "NORTH") ||
                    (result.back() == "WEST" && direction == "EAST") ||
                    (result.back() == "EAST" && direction == "WEST"))) {
                result.pop_back();
            }
            else {
                result.push_back(direction);
            }
        }
        return result;
    }
};
```
## Пример использования 

```C++
int main() {
    std::vector<std::string> directions1 = {"NORTH", "SOUTH", "SOUTH", "EAST", "WEST", "NORTH", "WEST"};
    std::vector<std::string> reduced1 = DirReduction::dirReduc(directions1);
    std::cout << "Reduced directions 1: "; // WEST
    for (const auto& dir : reduced1) {
        std::cout << dir << " ";
    }
    std::cout << std::endl;

    return 0;
}
```