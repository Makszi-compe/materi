---
title: Geometri
date: 23-03-2025 12:51
tags:
  - CPP
  - Competitive-Programming
  - "#Geometry"
  - Algorithm
  - Data-Structure
  - "#Convex-Hull"
  - "#Linear-Intersection"
---
# Geometri

## Deskripsi Singkat  
- **Geometri dalam pemrograman kompetitif** adalah cabang matematika yang berhubungan dengan **titik, garis, bidang, sudut, dan bentuk geometris lainnya** dalam ruang dua dimensi (2D) atau tiga dimensi (3D).

---

## Konsep Dasar Geometri dalam Competitive Programming
### Sistem Koordinat (Cartesian Coordinates)
- **Koordinat 2D:** `(x, y)`
- **Koordinat 3D:** `(x, y, z)`
- Contoh representasi titik dalam C++
```cpp
struct Point {
    double x, y;
};
```
### Jarak Antar Titik (Distance Formula)
- Rumus jarak antara dua titik `(x1, y1)` dan `(x2, y2)`:
$$d=\sqrt{(x2​−x1​)^2+(y2​−y1​)^2}​$$
- Implementasi di C++
``` cpp
#include <iostream>
#include <cmath>

using namespace std;

double distance(double x1, double y1, double x2, double y2) {
    return sqrt((x2 - x1) * (x2 - x1) + (y2 - y1) * (y2 - y1));
}

int main() {
    cout << distance(1, 2, 4, 6) << endl; // Output: 5
    
    return 0;
}
```
### Persamaan Garis Lurus
- Persamaan garis dalam bentuk **y = mx + c**, di mana:
	- **m** = kemiringan (slope)
	- **c** = intercept (nilai y saat x = 0)
- Cara mencari kemiringan antara dua titik
$$m=(y_2-y_1)/(x_2-x_1)$$
### Persamaan Lingkaran
- Persamaan lingkaran dengan pusat `(h, k)` dan jari-jari `r`:
$$r^2=(x-h)^2+(y-k)^2$$
### Perpotongan Dua Garis (Line Intersection)
- Jika dua garis **A** dan **B** bertemu di satu titik, kita bisa menghitungnya dengan:
$$ x = (b_2-b_1)/(m_1-m_2)$$
$$y=m_1x + b_1$$
### Cross Product dan Dot Product
- **Cross Product** digunakan untuk menentukan orientasi titik terhadap garis.
- **Dot Product** digunakan untuk mencari sudut antara dua vektor.
- **Jika hasil cross product positif → C ada di kiri AB, jika negatif → di kanan AB.**
- Cross Product dalam C++
```cpp
struct Point {
    double x, y;
};

double crossProduct(Point A, Point B, Point C) {
    return (B.x - A.x) * (C.y - A.y) - (B.y - A.y) * (C.x - A.x);
}
```

---

## Algoritma Penting dalam Geometri untuk Competitive Programming
### Convex Hull (Graham's Scan)
- Digunakan untuk mencari bentuk poligon cembung terkecil yang mencakup semua titik.
- Digunakan dalam Computational Geometry, Navigasi, dan Image Processing.
- **Kompleksitas Waktu:** **O(n log n)**
- Implementasi Convex Hull (Graham’s Scan) di C++
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

struct Point {
    int x, y;
    bool operator<(const Point& p) const { return x < p.x || (x == p.x && y < p.y); }
};

int crossProduct(Point A, Point B, Point C) {
    return (B.x - A.x) * (C.y - A.y) - (B.y - A.y) * (C.x - A.x);
}

vector<Point> convexHull(vector<Point>& points) {
    sort(points.begin(), points.end());
    vector<Point> hull;

    for (int phase = 0; phase < 2; phase++) {
        int start = hull.size();
        for (Point p : points) {
            while (hull.size() >= start + 2 &&
                   crossProduct(hull[hull.size() - 2], hull.back(), p) <= 0)
                hull.pop_back();
            hull.push_back(p);
        }
        hull.pop_back();
        reverse(points.begin(), points.end());
    }

    return hull;
}

int main() {
    vector<Point> points = {{0, 0}, {1, 1}, {2, 2}, {2, 0}, {1, -1}};
    vector<Point> hull = convexHull(points);
    
    for (Point p : hull) cout << "(" << p.x << ", " << p.y << ") ";
    
    return 0;
}
```
### Rotasi Titik (Rotation Transformation)
- Gunakan matriks rotasi untuk memutar titik sejauh sudut tertentu.
- Rumus Rotasi dengan Sudut `θ`
$$x'=x \cos \theta - y \sin \theta$$
$$y'=x \sin \theta - y \cos \theta$$
- Implementasi Rotasi Titik di C++
```cpp
#include <iostream>
#include <cmath>

using namespace std;

void rotatePoint(double x, double y, double theta) {
    double rad = theta * M_PI / 180.0; // Konversi ke radian
    double newX = x * cos(rad) - y * sin(rad);
    double newY = x * sin(rad) + y * cos(rad);
    cout << "Rotasi: (" << newX << ", " << newY << ")" << endl;
}

int main() {
    rotatePoint(1, 0, 90); // Output: (0, 1)
    
    return 0;
}
```

---

## Waktu Penggunaan
- **Gunakan Convex Hull jika**: Mencari poligon terkecil yang mencakup semua titik.
- **Gunakan Perpotongan Garis jika**: Butuh mengecek apakah dua garis saling bersinggungan.
- **Gunakan Rotasi jika**: Melakukan transformasi koordinat.
- **Gunakan Jarak Euclidean jika**: Menghitung jarak antar dua titik.