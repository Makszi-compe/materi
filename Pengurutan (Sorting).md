---
title: Pengurutan (Sorting)
date: 22-03-2025 22:42
tags:
  - Competitive-Programming
  - Algorithm
  - "#Sorting"
  - Data-Structure
  - "#Big-O-Notation"
---
# Pengurutan (Sorting)

## Deskripsi Singkat  
- Pengurutan (**sorting**) adalah proses menyusun elemen dalam suatu urutan tertentu, biasanya dalam **ascending (menaik)** atau **descending (menurun)**.

---

## Jenis - Jenis Algoritma Sorting
### Bubble Sort -> O(n²)
- **Cara kerja**: Bandingkan elemen berpasangan dan tukar jika tidak dalam urutan yang benar.
- **Kelebihan**: Mudah dipahami dan diimplementasikan.
- **Kekurangan**: Lambat untuk data besar (**O(n²)**).
### Selection Sort -> O(n²)
- **Cara kerja**: Pilih elemen terkecil, lalu tukar dengan posisi awal yang belum terurut.
- **Kelebihan**: Jumlah pertukaran lebih sedikit dibanding Bubble Sort.
- **Kekurangan**: Masih lambat untuk data besar (**O(n²)**).
### Insertion Sort -> O(n²)
- **Cara kerja**: Masukkan elemen satu per satu ke posisi yang benar dalam bagian yang sudah terurut.
- **Kelebihan**: Efektif untuk data kecil atau hampir terurut.
- **Kekurangan**: Masih lambat untuk data besar.
### Merge Sort -> O(n log n)
- **Cara kerja**:
	1. **Bagi** array menjadi dua bagian hingga tersisa elemen tunggal.
	2. **Urutkan** masing-masing bagian.
	3. **Gabungkan kembali** dengan mempertahankan urutan.
- **Kelebihan**: Selalu **O(n log n)**, cocok untuk data besar.
- **Kekurangan**: Menggunakan memori tambahan untuk penggabungan.
### Quick Sort -> O(n log n)
- - **Cara kerja**:
	1. Pilih **pivot** (biasanya elemen terakhir).
	2. **Pisahkan** elemen lebih kecil dan lebih besar dari pivot.
	3. **Rekursif** pada masing-masing bagian.
- **Kelebihan**: Sangat cepat untuk sebagian besar kasus.
- **Kekurangan**: Jika memilih pivot buruk, bisa menjadi **O(n²)**.
### Counting Sort -> O(n + k)
- **Cara kerja**: Menghitung frekuensi setiap elemen dan menyusun kembali.
- **Kelebihan**: Sangat cepat jika nilai elemen dalam rentang kecil.
- **Kekurangan**: Tidak cocok untuk nilai yang tersebar luas atau data bertipe float/negative.

---