# 7 kyu

## Buses!

https://www.codewars.com/kata/640dee7cbad3aa002e7c7de4/cpp

## Решение 

```C++
int buses(int kids, int adults, int places)
{
    // Если взрослых меньше двух или мест меньше трех, и при этом есть дети,
    // то автобусы не могут отправляться, и мы возвращаем 0.
    if ((adults < 2 || places < 3) && kids > 0)
        return 0;
    // Расчет количества автобусов, необходимых для перевозки детей(chbuss)
    int chbuss = (kids + places - 3) / (places - 2);
    // Расчет количества автобусов, необходимых для перевозки взрослых(adbuss)
    int adbuss = (adults) / 2;
    // Если количество автобусов, необходимых для перевозки детей, меньше или равно
    // количеству автобусов, необходимых для перевозки взрослых,
    // возвращаем количество автобусов, необходимых для перевозки всех пассажиров
    if (chbuss <= adbuss)
        return (kids + adults + places - 1) / places;

    return 0;
}
```
## Пример использования 

```C++
#include <iostream>

int main() {
    int kids = 2, adults = 4, places = 4;
    int num_buses = buses(kids, adults, places);
    std::cout << "Number of buses required: " << num_buses << std::endl;
    return 0;
}
```