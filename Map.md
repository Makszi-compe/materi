---
title: Map
date: 22-03-2025 10:35
tags:
  - CPP
  - STL
  - Data-Structure
---
# Map

## Deskripsi Singkat  
 - `map` dalam C++ Standard Template Library (STL) adalah struktur data asosiatif yang menyimpan elemen dalam bentuk **key-value pair (pasangan kunci-nilai)**.
 - Terdapat juga `unordered map`, perbedaannya secara default, elemen dalam `map` diurutkan berdasarkan key (ascending order) sementara dalam `unordered map` data tidak diurutkan.

---

## Operasi Dasar

| Operasi              | Keterangan                                   |
| -------------------- | -------------------------------------------- |
| insert({key, value}) | Menambahkan pasangan key-value ke dalam map. |
| erase(key)           | Menghapus elemen dengan key tertentu.        |
| find(key)            | Mencari elemen berdasarkan key.              |
| size()               | Mengembalikan jumlah elemen dalam map.       |
| empty()              | Mengecek apakah map kosong.                  |
| clear()              | Menghapus semua elemen dalam map.            |

---

## Source Code
```cpp
#include <iostream>
#include <map>

using namespace std;

int main() {
	map<string, string> myMap; // Deklarasi map dengan key-value berupa string

	// Menambahkan Elemen
	myMap["Apple"] = "Apel";
	myMap["Banana"] = "Pisang";
	myMap.insert({"Cherry", "Ceri"});

	for (auto pair: myMap) {
		cout << pair.first << " - " << pair.second << endl;
	}

	// Menghapus Elemen
	myMap.erase("Banana");

	for (auto pair: myMap) {
		cout << pair.first << " - " << pair.second << endl;
	}

	// Mencari Elemen
	auto it = myMap.find("Apple");
    
    if (it != myMap.end()) {
        cout << "Apple : " << it->second << endl;
    } else {
        cout << "Apple not found" << endl;
    }

	// Ukuran dan Pengecekan Kosong
	cout << "Size: " << myMap.size() << endl;
	cout << "Is empty? " << (myMap.empty() ? "Yes" : "No") << endl;
	
	return 0;
}