# 6 kyu

## longest_palindrome

https://www.codewars.com/kata/54bb6f887e5a80180900046b/cpp

## Решение 

```C++
int longest_palindrome(const std::string& s)
{
    int n = s.length();
    int max_len = 0;

    for (int i = 0; i < n; i++) {
        for (int j = 0; i - j >= 0 && i + j < n; j++) {
            if (s[i - j] != s[i + j]) break;
            int len = 2 * j + 1;
            if (len > max_len) max_len = len;
        }
    }
    for (int i = 0; i < n - 1; i++) {
        for (int j = 1; i - j + 1 >= 0 && i + j < n; j++) {
            if (s[i - j + 1] != s[i + j]) break;
            int len = 2 * j;
            if (len > max_len) max_len = len;
        }
    }
    return max_len;
}
```
## Пример использования 

```C++
int main()
{
    string input = "a";
    int expected_output = 1;
    
    int result = longest_palindrome(input);
    
    cout << "Input string: " << input << endl; 
    cout << "Expected output: " << expected_output << endl; // 1
    cout << "Actual output: " << result << endl; // 1
    
    if (result == expected_output) {
        cout << "Test case passed." << endl;
    } else {
        cout << "Test case failed." << endl;
    }
    
    return 0;
}
```
