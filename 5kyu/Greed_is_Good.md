# 5 kyu

## Greed is Good

https://www.codewars.com/kata/5270d0d18625160ada0000e4/cpp

## Решение 

```C++
int score(const std::vector<int>& dice)
{
    int score = 0;
    int count[7] = { 0 };

    for (int v : dice)
    {
        ++count[v];
        if (count[v] % 3 == 0)
        {
            score += (v == 1) ? 1000 : v * 100;
            count[v] = 0;
        }
    }

    score += count[1] * 100;
    score += count[5] * 50;

    return score;
}
```
## Пример использования 

```C++
int main()
{
    std::vector<int> dice1{2, 3, 4, 6, 2};
    int result1 = score(dice1);
    std::cout << "Score for dice1: " << result1 << std::endl; // 0

    std::vector<int> dice2{2, 4, 4, 5, 4};
    int result2 = score(dice2);
    std::cout << "Score for dice2: " << result2 << std::endl; // 450

    return 0;
}
```
