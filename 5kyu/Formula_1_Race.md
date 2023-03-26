# 5 kyu

## Formula 1 Race

https://www.codewars.com/kata/626d691649cb3c7acd63457b/cpp

## Решение 

```C++
#include <unordered_map>
#include <string>
#include <vector>

int ChampionRank(int pilot, const std::string& events) {
    // отображение пилота на его текущую позицию
    std::unordered_map<int, int> pilot_by_position;
    // отображение текущей позиции пилота на ней
    std::unordered_map<int, int> position_by_pilot;
    const int q_positions = 20;
    // номер последней занятой позиции
    int last_valid_position = q_positions;
    // список событий
    std::vector<std::string> events_list;

    std::string event;
    std::istringstream iss(events);
    // разбиваем строку на отдельные события
    while (iss >> event) {
        events_list.push_back(event);
    }
     // инициализация начальных значений отображений
    for (int i = 1; i <= q_positions; ++i) {
        pilot_by_position[i] = i;
        position_by_pilot[i] = i;
    }

    int i = 0;
    while (i < static_cast<int>(events_list.size()) - 1) {
        try {
            int id = std::stoi(events_list[i]);
            std::string e = events_list[i + 1];
            // событие - пилот выходит из гонки
            if (e == "I") {
                if (position_by_pilot[id] != -1) {
                    int old_position = position_by_pilot[id];
                    // отмечаем, что пилот больше не участвует в гонке
                    position_by_pilot[id] = -1;
                    // сдвигаем все последующие позиции
                    for (int j = old_position + 1; j <= last_valid_position; ++j) {
                        int id_aux = pilot_by_position[j];
                        position_by_pilot[id_aux] -= 1;
                        int pos_aux = position_by_pilot[id_aux];
                        // обновляем отображение позиции на пилота
                        pilot_by_position[pos_aux] = id_aux;
                    }
                    pilot_by_position[last_valid_position] = -1;
                    --last_valid_position;
                }
            }
            // событие - пилот обгоняет другого пилота
            else if (e == "O") {
                if (position_by_pilot[id] != -1 && position_by_pilot[id] != 1) {
                    // находим пилота, который занимает позицию на одну выше
                    int id_aux = pilot_by_position[position_by_pilot[id] - 1];
                    int best_position = position_by_pilot[id] - 1;
                    position_by_pilot[id] -= 1;
                    position_by_pilot[id_aux] += 1;

                    pilot_by_position[best_position] = id;
                    pilot_by_position[best_position + 1] = id_aux;
                }
            }
        }
        catch (...) 
        {
        }
        i += 2;
    }

    return position_by_pilot[pilot];
}
```
## Пример использования 

```C++
int main() {
    int pilot = 10;
    std::string events = "1 I 10 O 2 I";
    int rank = ChampionRank(pilot, events);
    std::cout << "Rank of pilot " << pilot << " is " << rank << std::endl; // 10
    return 0;
}
```
