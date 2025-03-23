---
title: List
date: 21-03-2025 16:54
tags:
  - "#CPP"
  - "#STL"
  - Linked-List
  - Data-Structure
---
# List

## Deskripsi Singkat  
- `list` adalah struktur data dalam C++ Standard Template Library (STL) yang mengimplementasikan doubly linked list.
- Lebih efisien untuk manipulasi data dibandingkan `vector`, tetapi kurang efisien untuk pencarian elemen secara langsung.

---

## Operasi Dasar
### Menambahkan Elemen
|    Operasi    |               Keterangan                |
|:-------------:|:---------------------------------------:|
| push_back(x)  |    Menambahkan elemen di akhir list.    |
| push_front(x) |    Menambahkan elemen di awal list.     |
| insert(it, x) | Menyisipkan elemen sebelum iterator it. |
### Menghapus Elemen
| Operasi     | Keterangan                               |
| ----------- | ---------------------------------------- |
| pop_back()  | Menghapus elemen terakhir                |
| pop_front() | Menghapus elemen pertama                 |
| erase(it)   | Menghapus elemen pada posisi iterator it |
| clear()     | Menghapus semua elemen dalam list        |
### Mengakses Elemen
- List tidak mendukung akses langsung seperti vector, jadi kita harus menggunakan iterator.
### Sorting dan Reverse
| Operasi   | Keterangan                              |
| --------- | --------------------------------------- |
| sort()    | Mengurutkan list dalam ascending order. |
| reverse() | Membalik urutan elemen dalam list       |
 
---

## Source Code
```cpp
#include <iostream>
#include <list>

using namespace std;

int main() {
    list<int> myList;

    // Menambahkan Elemen
    myList.push_back(10); // Tambah di depan
    myList.push_back(20); // Tambah di depan
    myList.push_back(50); // Tambah di depan
    myList.push_front(5); // Tambah di belakang
    myList.insert(next(myList.begin()), 7); // Sisipkan di posisi kedua

    for (int x : myList) {
        cout << x << " ";
    }
    cout << endl;
  
    // Menghapus Elemen
    myList.pop_back(); // Hapus elemen terakhir
    myList.pop_front(); // Hapus elemen pertama
    auto i = myList.begin();
    advance(i, 1); // Pindahkan iterator ke elemen kedua
    myList.erase(i); // Hapus elemen kedua

    for (int x : myList) {
        cout << x << " ";
    }
    cout << endl;
  
    // Mengakses Elemen
    list<int> newList = {30, 10, 40, 20, 50};
    list<int>::iterator it;
    for (it = newList.begin(); it != newList.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    // Mengurutkan Elemen
    newList.sort(); // Urutkan list
    newList.reverse(); // Balik urutan list

    for (it = newList.begin(); it != newList.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;
    
    return 0;
}