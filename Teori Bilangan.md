---
title: Teori Bilangan
date: 23-03-2025 13:47
tags:
  - "#Number-Theory"
  - Competitive-Programming
  - Algorithm
  - "#Mathematics"
  - "#Prime-Number"
  - "#GDC"
  - "#LCM"
  - "#Factorization"
---
# Teori Bilangan

## Deskripsi Singkat  
- **Teori Bilangan** adalah cabang matematika yang mempelajari **sifat dan hubungan antara bilangan bulat**.

---

## Konsep Dasar
### Faktor dan Kelipatan
- **Faktor (Divisors):** Bilangan yang habis membagi bilangan lain.
- **Kelipatan (Multiples):** Bilangan yang bisa diperoleh dengan mengalikan bilangan lain dengan suatu konstanta.
-  **Implementasi**: Mencari Semua Faktor dari N:
```cpp
#include <iostream>

using namespace std;

void findDivisors(int n) {
    for (int i = 1; i * i <= n; i++) {
        if (n % i == 0) {
            cout << i << " ";
            if (i != n / i) cout << (n / i) << " ";
        }
    }
}

int main() {
    findDivisors(12); // Output: 1 12 2 6 3 4
    
    return 0;
}
```
### Bilangan Prima dan Faktor Prima
 - **Bilangan Prima:** Bilangan yang hanya memiliki dua faktor, yaitu `1` dan dirinya sendiri.
 - **Bilangan Komposit:** Bilangan yang memiliki lebih dari dua faktor.
 - **Implementasi**: Cek Apakah Suatu Bilangan Prima:
```cpp
#include <iostream>

using namespace std;

bool isPrime(int n) {
    if (n < 2) return false;
    for (int i = 2; i * i <= n; i++)
        if (n % i == 0) return false;
    return true;
}

int main() {
    cout << isPrime(17); // Output: 1 (true)
    
    return 0;
}
```
- **Implementasi**: Sieve of Eratosthenes (Cari Semua Bilangan Prima ≤ N):
```cpp
#include <iostream>
#include <vector>

using namespace std;

void sieve(int n) {
    vector<bool> isPrime(n + 1, true);
    isPrime[0] = isPrime[1] = false;
    for (int i = 2; i * i <= n; i++) {
        if (isPrime[i]) {
            for (int j = i * i; j <= n; j += i)
                isPrime[j] = false;
        }
    }
    for (int i = 2; i <= n; i++)
        if (isPrime[i]) cout << i << " ";
}

int main() {
    sieve(50); // Output: 2 3 5 7 11 13 17 19 23 29 31 37 41 43 47
    
    return 0;
}
```
### FPB (GCD) dan KPK (LCM)
- GCD(a, b) = faktor terbesar yang membagi `a` dan `b` tanpa sisa. Rumus:
$$\gcd(a, b) = \gcd(b, a \bmod b)$$
- LCM(a, b) = Bilangan terkecil yang habis dibagi `a` dan `b`. Rumus:
$$\text{LCM}(a, b) = \frac{a \times b}{\gcd(a, b)}$$
- Implementasi GCD & LCM di C++ (Euclidean Algorithm)
```cpp
#include <iostream>

using namespace std;

int gcd(int a, int b) {
    return (b == 0) ? a : gcd(b, a % b);
}

int lcm(int a, int b) {
    return (a / gcd(a, b)) * b;
}

int main() {
    cout << gcd(48, 18) << endl; // Output: 6
    cout << lcm(48, 18) << endl; // Output: 144
    
    return 0;
}
```
### Modular Arithmetic (Modulo)
- Modular digunakan dalam perhitungan besar seperti kriptografi dan kombinatorika.
- Implementasi Fast Exponentiation (Modular Exponentiation)
```cpp
#include <iostream>

using namespace std;

long long modExp(long long base, long long exp, long long mod) {
    long long result = 1;
    while (exp > 0) {
        if (exp % 2 == 1) result = (result * base) % mod;
        base = (base * base) % mod;
        exp /= 2;
    }
    return result;
}

int main() {
    cout << modExp(2, 10, 1000000007) << endl; // Output: 1024
    
    return 0;
}
```

---

## Masalah yang Bisa Diselesaikan
- **Menentukan Bilangan Prima** → Gunakan **Sieve of Eratosthenes (O(n log log n))**.
- **Mencari FPB dan KPK** → Gunakan **Euclidean Algorithm (O(log n))**.
- **Modular Exponentiation** → Gunakan **Binary Exponentiation (O(log n))**.
- **Faktorisasi Prima Cepat** → Gunakan **Trial Division (O(√n)) atau Pollard’s Rho**.
- **Menemukan Invers Modular** → Gunakan **Extended Euclidean Algorithm**.

---