---
title: Tree
date: 22-03-2025 10:59
tags:
  - "#Data-Structure"
  - "#Tree"
---
# Tree

## Deskripsi Singkat  
 - `Tree` adalah **struktur data hierarkis** yang terdiri dari **simpul (node)** yang terhubung oleh **sisi (edge)**.
 - `Tree` bersifat **non-linear**, sehingga cocok untuk merepresentasikan hubungan **hirarki** seperti struktur organisasi, sistem file, atau pohon keputusan.

---

## Karakteristik
- **Berbentuk hierarkis** → Terdiri dari simpul induk (_parent_) dan anak (_child_).
- **Akar (`root`)** → Simpul paling atas tanpa induk.
- **Simpul Daun (`leaf`)** → Simpul yang tidak memiliki anak.
- **Tingkat (`level`)** → Jarak dari akar ke suatu simpul.
- **Tinggi (`height`)** → Jumlah tingkat dari akar hingga simpul terjauh.

---

## Terminologi dalam Tree

| Terminologi       | Penjelasan                                 |
| ----------------- | ------------------------------------------ |
| Root (Akar)       | Simpul paling atas dalam tree.             |
| Parent (Induk)    | Simpul yang memiliki satu atau lebih anak. |
| Child (Anak)      | Simpul yang memiliki induk.                |
| Leaf (Daun)       | SImpul tanpa anak.                         |
| Sibling (Saudara) | Simpul dengan induk yang sama.             |
| Degree            | Jumlah anak yang dimiliki simpul.          |
| Depth             | Jarak suatu simpul dari akar.              |
| Height            | Jarak simpul terjauh dari akar ke daun.    |

---

## Jenis - Jenis Tree
1. **Binary Tree** → Setiap simpul maksimal memiliki 2 anak.
2. **Binary Search Tree (BST)** → Versi terurut dari Binary Tree.
3. **Balanced Tree (AVL, Red-Black Tree)** → Pohon yang seimbang.
4. **Heap (Min Heap, Max Heap)** → Digunakan untuk _priority queue_.
5. **Trie (Prefix Tree)** → Digunakan untuk pencarian kata.
6. **Segment Tree** → Digunakan untuk pemrosesan range query.

---
