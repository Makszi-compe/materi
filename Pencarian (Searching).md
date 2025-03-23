---
title: Pencarian (Searching)
date: 23-03-2025 01:19
tags:
  - Competitive-Programming
  - "#Searching"
  - Data-Structure
  - Algorithm
---
# Pencarian (Searching)

## Deskripsi Singkat  
- **Searching (pencarian)** adalah proses menemukan **elemen tertentu dalam sebuah kumpulan data**.

---

## Jenis - Jenis Searching
### Pencarian Linear (Linear Search)
- Cara kerjanya mengecek setiap elemen dalam array satu per satu sampai elemen ditemukan.
- Bisa digunakan pada array yang tidak terurut.
- **Kompleksitas Waktu:** **O(n)** (karena harus mengecek setiap elemen).
- **Kelebihan:** **Mudah diterapkan**, bisa digunakan pada **array tidak terurut**.
- **Kekurangan:** Lambat jika data **sangat besar**.
### Pencarian Biner (Binary Search)
- Membandingkan **elemen tengah** dengan nilai yang dicari:
	- Jika lebih kecil → cari di kiri.
	- Jika lebih besar → cari di kanan.
	- Jika sama → elemen ditemukan.
- Digunakan pada array yang sudah terurut.
- **Kompleksitas Waktu:** **O(log n)**
- **Kelebihan:** **Jauh lebih cepat dibanding Linear Search**.
- **Kekurangan:** **Hanya bisa digunakan pada data yang sudah terurut**.
### Pencarian dengan Hashing
- Simpan data dalam **struktur hash table** sehingga pencarian bisa dilakukan dalam **O(1) rata-rata**.
- **Kompleksitas Waktu:** **O(1) rata-rata, O(n) worst case**
- **Kelebihan:** **Sangat cepat untuk pencarian key-value**.
- **Kekurangan:** **Menggunakan lebih banyak memori dibanding array biasa**.

---