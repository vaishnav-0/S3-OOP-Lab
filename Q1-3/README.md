## Question 1
❔ Write a program to check whether the given number is prime or not.

### Program

```cpp
#include <iostream>

int main() {
    int number;

    std::cout << "Enter the number to check :";
    std::cin >> number;

    for (int i = 2; i < sqrt(number); i++)
        if (!(number % i))
            return std::cout << "The number is not prime", 0;

    std::cout << "The entered number is prime";
    return 0;
}
```

### Algorithm

### Output

```text
Enter the number to check :123457
The entered number is prime
Process finished with exit code 0
```

![prime check output](outputs/prime_check.png)

## Question 2
❔ Write a program to find gcd of 2 numbers.

### Program

```cpp
#include <iostream>

int main() {
    int a, b;

    std::cout << "Enter the numbers to find GCD of\n";
    std::cin >> a >> b;

    if (!((a - b) * a * b))
        return std::cout << "GCD = " << (a != 0) * a + (a == 0) * b, 0;

    if (std::min(a, b) - a) {
        a += b;
        b = a - b;
        a = a - b;
    }

    for (int tmp; a; b = tmp) {
        tmp = a;
        a = b % a;
    }

    std::cout << "GCD = " << b;
    return 0;
}
```

### Algorithm

### Output

```text
Enter the numbers to find GCD of
 123 1234
GCD = 1
Process finished with exit code 0
```

![gcd output](outputs/gcd.png)

## Question 3
❔ Write a program to find last prime number before the entered input.

### Program

```cpp
#include <iostream>

int main() {
    int number;

    std::cout << "Enter the number under which you need the prime :";
    std::cin >> number;

    if (number < 3)
        return std::cout << "No primes less than " << number << " found", 0;

    int *primes = new int[number/2];
    int primes_found = 1;

    primes[0] = 2;

    for (int i = 3; i < number; i++) {
        bool prime = true;

        for (int j = 0; j < primes_found; j++)
            if (i % primes[j] == 0) {
                prime = false;
                break;
            }

        if (prime)
            primes[primes_found++] = i;
    }

    std::cout << "Largest prime < " << number << " = " << primes[primes_found - 1];

    delete[] primes;

    return 0;
}
```

### Algorithm

### Output

```text
Enter the number under which you need the prime :100
Largest prime < 100 = 97
Process finished with exit code 0
```

![max prime](outputs/max_prime.png)