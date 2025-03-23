---
title: Queue
date: 22-03-2025 10:15
tags:
  - CPP
  - STL
  - Data-Structure
---
# Queue

## Deskripsi Singkat  
- `queue` dalam C++ Standard Template Library (STL) adalah struktur data **FIFO (First In, First Out)**, di mana elemen yang **pertama masuk akan menjadi yang pertama keluar**

---

## Operasi Dasar

| Operasi | Keterangan                                       |
| ------- | ------------------------------------------------ |
| push(x) | Menambahkan elemen `x` ke belakang queue.        |
| pop()   | Menghapus elemen pertama (depan) queue.          |
| front() | Mengembalikan elemen pertama tanpa menghapusnya. |
| back()  | Mengembalikan elemen terakhir dalam queue        |
| size()  | Mengembalikan jumlah elemen dalam queue.         |
| empty() | Mengecek apakah queue kosong                     |

---

## Source Code
```cpp
#include <iostream>
#include <queue>

using namespace std;

int main() {
	queue<int> q;

	// Menambahkan Elemen
	q.push(10);
	q.push(20);
	q.push(30);
	q.push(40);
	q.push(50);

	cout << "Front element: " << q.front() << endl;
	cout << "Back element: " << q.back() << endl;

	// Menghapus Elemen
	q.pop();
	cout << "Front element after pop: " << q.front() << endl;

	// Mengecek Ukuran Queue
	cout << "Queue size: " << q.size() << endl;

	// Mengecek Apakah Queue Kosong
	cout << "Is empty? " << (q.empty() ? "Yes" : "No") << endl;
	
	return 0;
}