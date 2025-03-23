---
title: Algoritma Ad-Hoc
date: 22-03-2025 21:28
tags:
  - "#Competitive-Programming"
  - "#Algorithm"
  - "#Ad-Hoc"
  - "#Problem-Solving"
  - "#CPP"
---
# Algoritma Ad-Hoc

## Deskripsi Singkat  
- Algoritma **ad-hoc** adalah jenis algoritma yang tidak memiliki pendekatan umum atau pola yang baku.
- Solusi dibuat **khusus** berdasarkan pemahaman langsung terhadap masalah tanpa menggunakan algoritma standar seperti **Sorting, Graph, atau Dynamic Programming**.

---
## Waktu Penggunaan
- Ketika soal tidak memiliki pola atau struktur yang jelas.
- Jika solusi dapat ditemukan hanya dengan menerapkan aturan yang diberikan.
- Saat soal tidak membutuhkan algoritma kompleks seperti **Graph, DP, atau Greedy**.

---

## Tips
- **Baca dan pahami soal dengan baik** → Fokus pada pola dan aturan dalam soal.
- **Identifikasi apakah ada solusi langsung tanpa algoritma kompleks**.
- **Gunakan simulasi atau implementasi langsung** untuk menguji ide.
- **Perhatikan batasan input** → Kadang, implementasi brute-force cukup jika batasannya kecil.

---

## Contoh Penerapan
### Menentukan Bilangan Ganjil atau Genap
- Masalah: Diberikan bilangan N, tentukan apakah ganjil atau genap.
- Pendekatan Ad-Hoc: Langsung gunakan operator modulus (`%`).

```cpp
#include <iostream>

using namespace std;

int main() {
    int N;
    cin >> N;

    if (N % 2 == 0) {
        cout << "Genap" << endl;
    } else {
        cout << "Ganjil" << endl;
    }

    return 0;
}
```
### Simulasi Pergantian Lampu
- Masalah: Ada lampu yang hanya bisa dinyalakan dengan menekan tombol tertentu. Jika tombol ditekan N kali, apakah lampu menyala atau tidak jika awalnya mati?
- Pendekatan Ad-Hoc: Jika tombol ditekan ganjil kali = menyala, sedangkan jika genap kali = mati.

```cpp
#include <iostream>

using namespace std;

int main() {
    int N;
    cin >> N;

    if (N % 2 == 1) {
        cout << "Lampu Menyala" << endl;
    } else {
        cout << "Lampu Mati" << endl;
    }

    return 0;
}
```