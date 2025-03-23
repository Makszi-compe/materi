---
title: Rekursi
date: 23-03-2025 01:26
tags:
  - Competitive-Programming
  - "#Recursion"
  - Data-Structure
  - Algorithm
---
# Rekursi

## Deskripsi Singkat  
- **Rekursi** adalah teknik pemrograman di mana **sebuah fungsi memanggil dirinya sendiri** untuk menyelesaikan masalah.
- **Struktur dasar:**
	- **Base case** → Kondisi yang menghentikan rekursi.
	- **Recursive case** → Pemanggilan kembali fungsi dengan nilai lebih kecil.

---

## Tips
- Pastikan selalu ada "base case" agar tidak terjadi infinite loop.
- Gunakan memoization jika ada submasalah yang berulang (contoh: Fibonacci).
- Hindari rekursi dalam kasus yang bisa diselesaikan lebih cepat dengan iterasi.
- Gunakan `tail recursion` untuk mengoptimalkan penggunaan stack.

---

## Contoh Penerapan
### Menghitung Faktorial
- Faktorial dari `n` didefinisikan sebagai **`n! = n × (n-1)!`**
- Base case: `0! = 1`
```cpp
#include <iostream>
using namespace std;

int faktorial(int n) {
    if (n == 0) return 1; // Base case
    return n * faktorial(n - 1); // Recursive case
}
```
### Mencetak Angka dari `n` hingga 1
- **Base case:** Jika `n == 0`, berhenti.
- **Recursive case:** Cetak `n`, lalu panggil `rekursi(n - 1)`.
```cpp
#include <iostream>
using namespace std;

void cetak(int n) {
    if (n == 0) return; // Base case
    cout << n << " ";
    cetak(n - 1); // Recursive case
}
```
### Fibonacci
- Rumus fibonnaci ke-n:`F(n) = F(n-1) + F(n-2)`
- **Base case:** F(0) = 0 dan F(1) = 1
```cpp
// Fibonacci tanpa memoization
int fibonacci(int n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// Fibonacci dengan memoization
int dp[1000] = {0}; // Array untuk menyimpan hasil komputasi sebelumnya

int fibonacciMemo(int n) {
    if (n <= 1) return n;
    if (dp[n] != 0) return dp[n]; // Cek apakah sudah dihitung sebelumnya
    return dp[n] = fibonacciMemo(n - 1) + fibonacciMemo(n - 2);
}
```
### Depth First Search (DFS)
- DFS digunakan dalam pencarian graf dan pohon.
```cpp
#include <iostream>
#include <vector>

using namespace std;

vector<int> adj[100]; // Adjacency list
bool visited[100];    // Penanda node yang sudah dikunjungi

void dfs(int node) {
    visited[node] = true;
    cout << node << " ";

    for (int neighbor : adj[node]) {
        if (!visited[neighbor]) dfs(neighbor);
    }
}

int main() {
    adj[1] = {2, 3};
    adj[2] = {4, 5};
    adj[3] = {6};

    dfs(1); // Output: 1 2 4 5 3 6
    
    return 0;
}
```