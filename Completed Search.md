---
title: Completed Search
date: 23-03-2025 01:43
tags:
  - Competitive-Programming
  - "#Completed-Search"
  - "#Brute-Force"
  - "#Bakctraking"
  - "#Exhaustive-Search"
  - "#Recursion"
  - "#Combinatorics"
---
# Completed Search

## Deskripsi Singkat  
- **Completed Search** adalah teknik eksplorasi **seluruh kemungkinan solusi** untuk menemukan hasil terbaik dalam suatu masalah.
- Ini adalah pencarian **brute force yang sistematis** untuk memastikan semua solusi diperiksa.
- **Digunakan ketika jumlah kemungkinan solusi masih cukup kecil (`≤ 10⁷`)** sehingga eksplorasi lengkap masih efisien.
- **Sering digunakan dalam**:
	- **Backtracking** (DFS dengan eksplorasi semua jalur).
	- **Generate semua permutasi, kombinasi, atau subset**.
	- **Brute force dengan optimasi pruning**.

---

## Jenis - Jenis Completed Search
### Brute Force (Exhaustive Search)
- Coba **semua kemungkinan solusi** dan cek mana yang memenuhi syarat.
- Efektif jika jumlah kemungkinan kecil (`n ≤ 10⁷`).
- Contoh: Mencari pasangan `(x, y)` yang memenuhi `x + y = 10` untuk `x, y` dalam **array kecil**.
```cpp
#include <iostream>

using namespace std;

void cariPasangan(int arr[], int n, int target) {
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (arr[i] + arr[j] == target) {
                cout << "Pasangan: " << arr[i] << ", " << arr[j] << endl;
            }
        }
    }
}

int main() {
    int arr[] = {1, 2, 3, 7, 8, 9};
    int n = sizeof(arr) / sizeof(arr[0]);
    cariPasangan(arr, n, 10);
    
    return 0;
}
```
### Generate Semua Subset
- **Gunakan rekursi atau bitmasking** untuk menghasilkan **semua subset dari suatu array**.
- Digunakan dalam masalah knapsack, kombinasi angka, atau pemilihan optimal.
```cpp
#include <iostream>
#include <vector>

using namespace std;

vector<int> subset;
void generateSubset(int arr[], int n, int idx) {
    if (idx == n) {
        cout << "{ ";
        for (int num : subset) cout << num << " ";
        cout << "}\n";
        return;
    }

    // Tidak memasukkan elemen ke subset
    generateSubset(arr, n, idx + 1);

    // Memasukkan elemen ke subset
    subset.push_back(arr[idx]);
    generateSubset(arr, n, idx + 1);
    subset.pop_back();
}

int main() {
    int arr[] = {1, 2, 3};
    int n = sizeof(arr) / sizeof(arr[0]);
    generateSubset(arr, n, 0);
    
    return 0;
}
```
### Generate Semua Permutasi (Backtracking)
- Menghasilkan semua kemungkinan urutan elemen dari suatu array.
- Digunakan dalam masalah seperti Traveling Salesman Problem (TSP).
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

void generatePermutations(vector<int>& nums, int idx) {
    if (idx == nums.size()) {
        for (int num : nums) cout << num << " ";
        cout << endl;
        return;
    }

    for (int i = idx; i < nums.size(); i++) {
        swap(nums[idx], nums[i]);
        generatePermutations(nums, idx + 1);
        swap(nums[idx], nums[i]); // Backtrack
    }
}

int main() {
    vector<int> nums = {1, 2, 3};
    generatePermutations(nums, 0);
    return 0;
}

```

---

## Optimasi Completed Search
- **Pruning (Pemangkasan)** → Hentikan eksplorasi jika sudah pasti salah.
- **Memoization** → Simpan hasil perhitungan agar tidak dihitung ulang.
- **Sorting + Binary Search** → Gunakan pencarian biner jika memungkinkan.
- Contoh backtracking dengan pruning (8-queens problem):
```cpp
#include <iostream>

using namespace std;

int board[8], solusi = 0;

bool isValid(int row, int col) {
    for (int i = 0; i < row; i++) {
        if (board[i] == col || abs(board[i] - col) == abs(i - row)) return false;
    }
    return true;
}

void solveNQueens(int row) {
    if (row == 8) {
        solusi++;
        return;
    }

    for (int col = 0; col < 8; col++) {
        if (isValid(row, col)) {
            board[row] = col;
            solveNQueens(row + 1);
        }
    }
}

int main() {
    solveNQueens(0);
    cout << "Total solusi: " << solusi << endl;
    
    return 0;
}
```

---

## Waktu Penggunaan
- Jika **jumlah kemungkinan solusi masih kecil (`≤ 10⁷`)**.
- Jika **tidak ada algoritma yang lebih optimal** (misalnya, tidak bisa menggunakan DP atau Greedy).
- Jika **ingin memastikan semua solusi dicoba (misalnya dalam masalah kombinatorik).**
- Hindari Completed Search jika jumlah solusi terlalu besar (`n > 10⁷`). Gunakan **Dynamic Programming (DP), Greedy, atau Binary Search** sebagai alternatif.

---
