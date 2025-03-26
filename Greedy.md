---
title: Greedy
date: 23-03-2025 13:37
tags:
  - Algorithm
  - "#Greedy-Algorithm"
  - Competitive-Programming
  - Knapsack
  - "#Huffman-Coding"
  - "#Heap"
  - CPP
---
# Greedy

## Deskripsi Singkat
- **Algoritma Greedy (Serakah)** adalah pendekatan dalam pemrograman yang memilih **solusi terbaik pada setiap langkah** dengan harapan hasil akhirnya juga optimal.
- Ciri utama Greedy:
	- **Local Optimal Choice** → Selalu memilih solusi terbaik pada setiap langkah.
	- **No Backtracking** → Tidak mempertimbangkan keputusan sebelumnya.
	- **Fast and Efficient** → Biasanya lebih cepat dibanding DP atau Brute Force.
- Karakteristik Masalah yang Bisa Diselesaikan dengan Greedy:
	- **Greedy Choice Property** → Solusi optimal global dapat diperoleh dengan memilih langkah optimal lokal setiap saat.
	- **Optimal Substructure** → Solusi optimal dari masalah besar dapat dibangun dari solusi optimal submasalahnya.

---

## Implementasi Algoritma Greedy
### Coin Change Problem
- **Masalah:**  Diberikan koin `{1, 5, 10, 25, 50}` dan jumlah uang `N`, cari jumlah koin minimum untuk mencapai `N`.
- **Solusi Greedy:** Pilih **koin terbesar yang masih memungkinkan** setiap saat.
- **Kompleksitas Waktu:** **O(N / minCoin)**
- Ilustrasi:
```css
N = 67
Gunakan 50 → Sisa 17
Gunakan 10 → Sisa 7
Gunakan 5 → Sisa 2
Gunakan 1 → Sisa 1
Gunakan 1 → Sisa 0
Total: 5 koin
```
- Implementasi di C++
```cpp
#include <iostream>
#include <vector>

using namespace std;

void minCoins(vector<int>& coins, int N) {
    vector<int> result;
    for (int coin : coins) {
        while (N >= coin) {
            N -= coin;
            result.push_back(coin);
        }
    }
    for (int c : result) cout << c << " ";
}

int main() {
    vector<int> coins = {50, 25, 10, 5, 1};
    int N = 67;
    minCoins(coins, N); // Output: 50 10 5 1 1
    
    return 0;
}
```
### Activity Selection Problem (Interval Scheduling)
- **Masalah:** Diberikan `n` kegiatan `(start, end)`, pilih **jumlah maksimum kegiatan** tanpa bertabrakan.
- **Solusi Greedy:**
	1. Urutkan kegiatan berdasarkan waktu selesai.
	2. Pilih kegiatan yang selesai paling awal yang tidak bertabrakan dengan yang dipilih sebelumnya.
- **Kompleksitas Waktu:** **O(n log n)** (karena sorting).
- Implementasi di C++
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

struct Activity {
    int start, end;
};

bool compare(Activity a, Activity b) {
    return a.end < b.end;
}

void maxActivities(vector<Activity>& activities) {
    sort(activities.begin(), activities.end(), compare);
    int count = 1, lastEnd = activities[0].end;
    
    for (int i = 1; i < activities.size(); i++) {
        if (activities[i].start >= lastEnd) {
            count++;
            lastEnd = activities[i].end;
        }
    }
    cout << "Maksimum kegiatan yang bisa dilakukan: " << count << endl;
}

int main() {
    vector<Activity> activities = {{1, 3}, {2, 5}, {3, 9}, {6, 8}};
    maxActivities(activities); // Output: Maksimum kegiatan = 2
    
    return 0;
}
```
### Huffman Coding (Data Compression)
- **Masalah:** Kompresi data dengan membuat kode variabel panjang berdasarkan **frekuensi karakter**.
- **Solusi Greedy:**
	1. Gunakan Heap (Priority Queue) untuk memilih karakter dengan frekuensi terendah.
	2. Bentuk pohon Huffman untuk membuat kode biner.
- **Kompleksitas Waktu:** **O(n log n)**
- Implementasi Huffman Coding di C++
```cpp
#include <iostream>
#include <queue>

using namespace std;

struct Node {
    char ch;
    int freq;
    Node* left, *right;
    Node(char c, int f) : ch(c), freq(f), left(NULL), right(NULL) {}
};

struct Compare {
    bool operator()(Node* a, Node* b) {
        return a->freq > b->freq;
    }
};

void huffmanCoding(vector<pair<char, int>> chars) {
    priority_queue<Node*, vector<Node*>, Compare> pq;
    
    for (auto ch : chars) pq.push(new Node(ch.first, ch.second));
    
    while (pq.size() > 1) {
        Node* left = pq.top(); pq.pop();
        Node* right = pq.top(); pq.pop();
        Node* merged = new Node('*', left->freq + right->freq);
        merged->left = left;
        merged->right = right;
        pq.push(merged);
    }
    
    cout << "Huffman Tree Created!" << endl;
}

int main() {
    vector<pair<char, int>> chars = {{'a', 5}, {'b', 9}, {'c', 12}, {'d', 13}};
    huffmanCoding(chars);
    
    return 0;
}
```

---
## Waktu Penggunaan
 - Masalah memiliki Greedy Choice Property dan Optimal Substructure.
 - Perlu solusi cepat dengan kompleksitas lebih rendah.

---
