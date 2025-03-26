---
title: Pemrograman Dinamis
date: 23-03-2025 13:20
tags:
  - "#Dynamic-Programming"
  - Competitive-Programming
  - Algorithm
  - "#Memoization"
  - "#Tabulation"
  - "#Recursion"
  - "#Knapsack"
  - "#Fibonacci"
  - CPP
---
# Pemrograman Dinamis

## Deskripsi Singkat  
- **Pemrograman Dinamis (Dynamic Programming, DP)** adalah teknik pemrograman yang menyelesaikan masalah dengan **memecahnya menjadi submasalah yang lebih kecil**, menyimpan hasilnya, dan menggunakan kembali hasil tersebut untuk menghindari perhitungan ulang.
- Ciri utama DP:
	- **Overlapping Subproblems** → Masalah besar dapat dipecah menjadi submasalah yang berulang.
	- **Optimal Substructure** → Solusi optimal dari masalah besar bisa didapatkan dari solusi optimal submasalahnya.

---

## Teknik Pemrograman Dinamis
### Top-Down (Memoization)
- Menggunakan **rekursi** dan **menyimpan hasil submasalah dalam array atau hashmap**.
- Cocok jika banyak submasalah yang tidak terpakai (sparse computation).
- Mirip rekursi biasa tapi dengan caching hasilnya.
- Gunakan Top-Down jika: Hanya sebagian kecil submasalah yang digunakan.
### Bottom-Up (Tabulation)
- Menggunakan **iterasi untuk membangun solusi dari submasalah kecil ke besar**.
- Lebih efisien dalam penggunaan memori dibandingkan memoization.
- Menghindari overhead rekursi.
-  Gunakan Bottom-Up jika: Semua submasalah dibutuhkan dan ingin menghemat memori.

---

## Implementasi Pemrograman Dinamis
### Fibonacci dengan Top-Down (Memoization)
- Gunakan array `dp[]` untuk menyimpan hasil yang sudah dihitung.
- **Kompleksitas Waktu:** **O(n)**
```cpp
#include <iostream>

using namespace std;

int dp[1000]; // Array untuk menyimpan hasil komputasi sebelumnya

int fibonacci(int n) {
    if (n <= 1) return n;
    if (dp[n] != 0) return dp[n]; // Cek apakah sudah dihitung sebelumnya
    return dp[n] = fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
    cout << fibonacci(10); // Output: 55
    
    return 0;
}
```
### Fibonacci dengan Bottom-Up (Tabulation)
- Gunakan array untuk menyimpan hasil dari `F(0)` hingga `F(n)`.
- **Kompleksitas Waktu:** **O(n)**
```cpp
#include <iostream>

using namespace std;

int fibonacci(int n) {
    int dp[n + 1]; // Array untuk menyimpan hasil
    dp[0] = 0, dp[1] = 1;
    for (int i = 2; i <= n; i++)
        dp[i] = dp[i - 1] + dp[i - 2];

    return dp[n];
}

int main() {
    cout << fibonacci(10); // Output: 55
    
    return 0;
}
```

---

## Masalah yang Dapat Diselesaikan
### Knapsack Problem (0/1 Knapsack)
- Masalah:
	- Diberikan `n` barang dengan berat `w[i]` dan nilai `v[i]`.
	- Pilih barang untuk **memaksimalkan total nilai** tanpa melebihi batas berat `W`.
- **Kompleksitas:** **O(nW)**
- Rumus Rekurens:
$$dp[i][w] = \max(dp[i-1][w], dp[i-1][w-w_i] + v_i)$$
### Longest Common Subsequence (LCS
- Masalah: Temukan panjang subsekuensi terpanjang yang **muncul secara berurutan dalam dua string**.
- **Kompleksitas:** **O(nm)**
- Rumus Rekurens:
$$dp[i][j] =
\begin{cases} 
1 + dp[i-1][j-1], & \text{jika } s1[i] = s2[j] \\ 
\max(dp[i-1][j], dp[i][j-1]), & \text{jika tidak sama} 
\end{cases}$$
## Subset Sum Problem
- Masalah: Apakah mungkin memilih beberapa angka dari array agar jumlahnya sama dengan `target`?
- **Kompleksitas:** **O(nW)**
- Rumus Rekurens:
$$dp[i][\text{sum}] =
\begin{cases} 
dp[i-1][\text{sum}], & \text{tidak memilih angka ke-}i \\ 
dp[i-1][\text{sum} - arr[i]], & \text{memilih angka ke-}i 
\end{cases}$$

---

## Waktu Penggunaan
- **Masalah memiliki Overlapping Subproblems** (misalnya, Fibonacci, LCS, Knapsack).
- **Ada Optimal Substructure** (solusi besar bisa dibangun dari solusi kecil).
- **Butuh optimasi perhitungan** untuk menghindari perhitungan berulang.

---

