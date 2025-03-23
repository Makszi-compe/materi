---
title: Struktur Data
date: 22-03-2025 21:39
tags:
  - Data-Structure
  - Competitive-Programming
  - Big-O-Notation
---
# Struktur Data

## Deskripsi Singkat  
- Struktur data adalah cara menyimpan dan mengorganisir data agar bisa diakses dan dimanipulasi dengan efisien.

---

## Struktur Data Sederhana
### Array
- Definisi: Kumpulan elemen dengan tipe data yang sama, disimpan dalam indeks berurutan.
- Operasi Utama:
	1. **Akses elemen** → `O(1)`
	2. **Update elemen** → `O(1)`
	3. **Pencarian (Linear Search)** → `O(n)`
- Kelebihan: Akses cepat ke elemen dengan indeks.
- Kekurangan: Ukuran tetap dan sulit untuk diubah.
### Linked List
- Definisi: Kumpulan node yang saling terhubung melalui pointer.
- Operasi Utama:
	1. **Penambahan node di awal** → `O(1)`
	2. **Penambahan di tengah/akhir** → `O(n)`
	3. **Pencarian** → `O(n)`
- Kelebihan: Mudah menambah/menghapus elemen tanpa menggeser elemen lain.
- Kekurangan: Akses elemen lebih lambat dibandingkan array karena harus traversing dari awal.
### Stack
- Definisi: Strukutur data **LIFO (Last In, FIrst Out)**.
- Operasi Utama:
	1. **Push (menambah elemen)** → `O(1)`
	2. **Pop (menghapus elemen terakhir)** → `O(1)`
	3. **Top (melihat elemen terakhir)** → `O(1)`
- Kelebihan: Cocok untuk undo/redo, DFS, dan evaluasi ekspresi.
- Kekurangan: Tidak bisa mengakses elemen selain yang di atas.
### Queue
- Definisi: Struktur data **FIFO (First In, First Out)**.
- Operasi Utama:
	1. **Enqueue (menambah elemen)** → `O(1)`
	2. **Dequeue (menghapus elemen pertama)** → `O(1)`
- Kelebihan: Berguna untuk BFS, sistem antrian, dan schedulling.
- Kekurangan: Hanya bisa mengakses elemen dari depan atau belakang.

---

## Strukutur Data Lanjutan
### Heap (Priority Queue)
- Definisi: Strukutur data berbasis binary heap yang mengelola elemen berdasarkan prioritas.
- Operasi utama:
	1. **Insert** → `O(log n)`
	2. **Extract Min/Max** → `O(log n)`
	3. **Peek (lihat elemen prioritas tertinggi)** → `O(1)`
- Kelebihan: Efisien untuk mencari nilai maksimum/minimum.
- Kekurangan: Tidak bisa mengakses elemen sembarang dengan cepat.
### HashMap (Unordered Map)
- Definisi: Struktur data yang menyimpan data dalam pasangan **key-value** dengan hashing.
- Operasi utama:
	1. **Insert** → `O(1)` (rata-rata)
	2. **Insert** → `O(1)` (rata-rata)
	3. **Delete** → `O(1)` (rata-rata)
- Kelebihan: Akses data sangat cepat.
- Kekurangan: Tidak Terurut.
### Graph (Graf)
- Definisi: Kumpulan **node/vertex** yang terhubung dengan **edge (sisi)**.
- Kelebihan: Berguna untuk masalah **Graph Theory**, seperti BFS, DFS, Dijkstra, dll.
- Kekurangan: Implementasi bisa kompleks.
### Segment Tree
- Definisi: Pohon biner untuk **range query** (misalnya mencari jumlah atau maksimum dalam rentang tertentu).
- Operasi utama:
	1. **Build Tree** → `O(n)`
	2. **Update** → `O(log n)`
	3. **Query (misal, sum atau min/max dalam range)** → `O(log n)`
- Kelebihan: Cepat untuk range query.
- Kekurangan: Implementasi lebih rumit dibandingkan array biasa.

---