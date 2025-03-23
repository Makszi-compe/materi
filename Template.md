---
title: Template
date: 21-03-2025 16:15
tags:
  - "#CPP"
  - "#STL"
---
# Template

## Deskripsi Singkat  
- Templates dalam C++ adalah fitur yang memungkinkan kita menulis kode generik sehingga dapat bekerja dengan berbagai tipe data tanpa harus menulis ulang kode untuk setiap tipe.
- Terdapat dua jenis template, yaitu **Function Templates** dan **Class Templates**.

---

## Source Code
```cpp
#include <iostream>

using namespace std;

// Function Templates
template <typename T>
T maxValue(T a, T b) {
    return (a > b) ? a : b;
}

// Class Templates
template <typename T>
class Calculator {
public:
    T add (T a, T b) {
        return a + b;
    }
};

int main() {
    cout << maxValue(5, 6) << endl;
    
    Calculator<int> intCal;
    Calculator<float> floatCal;

    cout << intCal.add(5, 4) << endl;
    cout << floatCal.add(5.2, 4.1) << endl;
	
	return 0;
}