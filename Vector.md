---
title: Vector
date: 21-03-2025 23:48
tags:
  - CPP
  - STL
  - Data-Structure
---
# Vector

## Deskripsi Singkat  
- `vector` adalah struktur data dinamis dalam Standard Template Library (STL) C++ yang berfungsi sebagai array dinamis.

---

## Operasi Dasar
### Menambahkan Elemen

| Operasi       | Keterangan                                |
| ------------- | ----------------------------------------- |
| push_back()   | Menambahkan elemen x ke akhir vector.     |
| insert(it, x) | Menyisipkan elemen x sebelum iterator it. |
### Menghapus Elemen

| Operasi    | Keterangan                         |
| ---------- | ---------------------------------- |
| pop_back() | Menghapus elemen terakhir.         |
| erase(it)  | Menghapus elemen pada iterator it. |
| clear()    | Menghapus semua elemen             |
### Mengakses Elemen
```cpp
cout << vec[2] << endl; // Akses langsung seperti array
cout << vec.at(2) << endl; // Akses dengan pengecekan batas
```

### Iterasi Menggunakan Iterator
```cpp
vector<int> vec = {10, 20, 30, 40};
vector<int>::iterator it;
for (it = vec.begin(); it != vec.end(); ++it) {
	cout << *it << " ";
}
```
### Mengecek Ukuran dan Kapasitas

| Operasi    | Keterangan                                                         |
| ---------- | ------------------------------------------------------------------ |
| size()     | Mengembalikan jumlah elemen dalam vector.                          |
| capacity() | Mengembalikan kapasitas maksimum sebelum perlu dialokasikan ulang. |
| empty()    | Mengecek apakah vector kosong.                                     |
### Sorting
- Gunakan fungsi `sort()` dari `<algorithm>` untuk mengurutkan `vector`.
```cpp
vector<int> vec = {30, 10, 50, 20 ,40};
sort(vec.begin(), vec.end()); // Urutkan secara ascending
for (int x : vec) {
		cout << x << " ";
}
```

---

## Source Code
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main() {
    vector<int> vec;

    // Menambah Elemen
    vec.push_back(10); // Tambah di belakang
    vec.push_back(60);
    vec.push_back(80);
    vec.push_back(30);
    vec.push_back(40);
    vec.insert(vec.begin(), 5); // Tambah di posisi pertama
  
    for (int x : vec) {
        cout << x << " ";
    }
    cout << endl;

    // Menghapus Elemen
    vec.pop_back(); // Hapus elemen terakhir
    vec.erase(vec.begin()); // Hapus elemen pertama

    for (int x : vec) {
        cout << x << " ";
    }
    cout << endl;
  
    // Mengakses Elemen
    cout << vec[1] << endl; // Akses langsung
    cout << vec.at(1) << endl; // Akses dengan pengecekan batas
    // Iterasi Menggunakan Iterator
    for (auto it = vec.begin(); it != vec.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    // Mengecek Ukuran dan Kapasitas
    cout << "Size: " << vec.size() << endl;
    cout << "Capacity: " << vec.capacity() << endl;
    cout << "Is Empty? " << (vec.empty() ? "Yes" : "No") << endl;

    // Sorting
    sort(vec.begin(), vec.end()); // Urutkan secara ascending
    
    for (int x : vec) {
        cout << x << " ";
    }
    cout << endl;

    return 0;
}