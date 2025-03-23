---
title: Stack
date: 22-03-2025 01:14
tags:
  - CPP
  - STL
  - Data-Structure
---
# Stack

## Deskripsi Singkat  
- `stack` dalam C++ Standard Template Library (STL) adalah struktur data **LIFO (Last In, First Out)**, di mana **elemen yang terakhir dimasukkan adalah elemen yang pertama keluar.**

---

## Operasi Dasar
| Operasi | Keterangan                                       |
| ------- | ------------------------------------------------ |
| push(x) | Menambahkan elemen `x` ke atas stack.            |
| pop()   | Menghapus elemen teratas stack.                  |
| top()   | Mengembalikan elemen teratas tanpa menghapusnya. |
| size()  | Mengembalikan jumlah elemen dalam stack.         |
| empty() | Mengecek apakah stack kosong.                    |

---

## Source Code
```cpp
#include <iostream>
#include <stack>

using namespace std;

int main() {
	stack<int> s;

	// Menambahkan Elemen
	s.push(10);
	s.push(20);
	s.push(30);
	s.push(40);

	cout << "Top Elemen: " << s.top() << endl;
	
	// Menghapus Elemen
	s.pop();
	cout << "Top Elemen: " << s.top() << endl;

	// Mengecek Ukuran Stack
	cout << "Stack Size: " << s.size() << endl;

	// Mengecek Apakah Stack Kosong
	cout << "Apakah Kosong: " << (s.empty() ? "Yes" : "No");

	return 0;
}