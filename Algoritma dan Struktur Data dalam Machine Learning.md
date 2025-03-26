---
title: Algoritma dan Struktur Data dalam Machine Learning
date: 23-03-2025 02:23
tags:
  - Algorithm
  - "#Machine-Learning"
  - Competitive-Programming
  - Data-Structure
  - "#Graph"
  - "#Data-Science"
  - "#KNN"
  - "#Heap"
  - "#Tree"
  - CPP
---
# Algoritma dan Struktur Data dalam Machine Learning

## Deskripsi Singkat  
- **Machine Learning (ML)** adalah cabang dari kecerdasan buatan (AI) yang memungkinkan komputer untuk **belajar dari data** tanpa diprogram secara eksplisit.

---

## Struktur Data dalam Machine Learning

| Struktur Data                       | Digunakan dalam                                                          |
| ----------------------------------- | ------------------------------------------------------------------------ |
| Matrix & Tensor                     | Representasi data dalam Neuran Networks.                                 |
| Heap & Priority Order               | K-Nearest Neighbors (KNN), Decision Tree Optimization.                   |
| Graph                               | Representasi hubungan antar data dalam Neural Network, Bayesian Network. |
| Tree (Decision Tree, Random Forest) | Klasifikasi dan regresi                                                  |
| Hash Table                          | Menyimpan cache untuk percepatan inferensi                               |

---

## Algoritma dalam Machine Learning
### K-Nearest Neighbors (KNN) dengan Heap & Priority Queue
- KNN menentukan kelas suatu titik berdasarkan **k tetangga terdekatnya**.
- **Heap digunakan untuk mempercepat pencarian tetangga terdekat** dalam kompleksitas **O(n log k)**.
- **Kompleksitas Waktu:** **O(n log k)**, lebih cepat dibandingkan brute force O(n²).
```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <cmath>

using namespace std;

struct Point {
    double x, y;
    double distance() const { return sqrt(x * x + y * y); }
};

vector<Point> findKClosest(vector<Point>& points, int k) {
    priority_queue<pair<double, Point>> maxHeap;
    for (Point p : points) {
        maxHeap.push({p.distance(), p});
        if (maxHeap.size() > k) maxHeap.pop();
    }
    
    vector<Point> result;
    while (!maxHeap.empty()) {
        result.push_back(maxHeap.top().second);
        maxHeap.pop();
    }
    return result;
}

int main() {
    vector<Point> points = {{3, 3}, {5, -1}, {-2, 4}};
    vector<Point> closest = findKClosest(points, 2);
    for (Point p : closest) cout << "(" << p.x << ", " << p.y << ") ";
    
    return 0;
}
```
### Decision Tree untuk Klasifikasi dan Regresi
- Decision Tree membagi dataset berdasarkan fitur untuk membuat keputusan.
- Struktur data Tree digunakan untuk menyimpan aturan klasifikasi.
- Digunakan dalam algoritma ID3, CART, dan Random Forest.
- Contoh Struktur Decision Tree.
```markdown
       Outlook
       /    \
   Sunny    Rainy
   /   \      |
High  Normal  Low
```
### Neural Network dengan Graph dan Matrix
- Neural Network terdiri dari **node dan edge**, sehingga direpresentasikan sebagai **Graph**.
- Setiap layer adalah matrix (tensor) yang digunakan untuk perhitungan.
- Digunakan dalam Deep Learning untuk pengenalan pola dan prediksi.
- Contoh Representasi Neural Network:
```markdown
  Input → Hidden Layer → Output
     \       | | |       /
      \      | | |      /
       → (Neuron dengan bobot) →
```
### K-Means Clustering dengan Hash Table
- Mengelompokkan data berdasarkan jarak ke pusat kluster.
- K-Means digunakan dalam pengelompokan data tanpa label.
- Implementasi K-Means Sederhana di C++
```cpp
#include <iostream>
#include <vector>
#include <cmath>

using namespace std;

vector<double> centroids = {2.0, 8.0};

int getNearestCluster(double x) {
    return abs(x - centroids[0]) < abs(x - centroids[1]) ? 0 : 1;
}

int main() {
    vector<double> data = {1.5, 2.5, 7.0, 9.0};
    for (double x : data) {
        cout << "Data " << x << " masuk ke cluster " << getNearestCluster(x) << endl;
    }
    
    return 0;
}
```

## Waktu Penggunaan
- **Gunakan KNN jika**: Butuh klasifikasi berbasis jarak (misalnya, rekomendasi).
- **Gunakan Decision Tree jika**: Butuh model berbasis aturan untuk klasifikasi atau regresi.
- **Gunakan Graph jika**: Menganalisis hubungan antar data (misalnya dalam jaringan sosial).
- **Gunakan Hash Table jika**: Butuh penyimpanan cepat untuk hasil pengelompokan data.

---