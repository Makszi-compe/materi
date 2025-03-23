---
title: Binary Search Tree
date: 22-03-2025 20:33
tags:
  - Binary-Tree
  - Data-Structure
  - Tree
  - "#Binary-Search-Tree"
---
# Binary Search Tree

## Deskripsi Singkat  
- **Binary Search Tree (BST)** adalah jenis **Binary Tree** yang memiliki aturan khusus:
	1. Simpul kiri (`left`) memiliki nilai lebih kecil dari induknya (`parent`).
	2. Simpul kanan (`right`) memiliki nilai lebih besar dari induknya.
	3. Tidak ada nilai yang duplikat dalam BST.

---

## Operasi Dasar

| Operasi           | Keterangan                                            |
| ----------------- | ----------------------------------------------------- |
| Insert(x)         | Menambahkan nilai `x` ke BST.                         |
| Search(x)         | Mencari nilai `x` di dalam BST.                       |
| Delete(x)         | Menghapus nilai `x` dari BST.                         |
| Inorder Traversal | Menampilkan BST dalam **urut naik (ascending order)** |

---

## Source Code
```cpp
#include <iostream>

using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;

    Node(int val) {
        data = val;
        left = right = NULL;
    }
};

// Fungsi Menambahkan Elemen
Node* insert(Node* root, int val) {
    if (root == NULL) return new Node(val);

    if (val < root->data)
        root->left = insert(root->left, val);
    else
        root->right = insert(root->right, val);
    
    return root;
}

// Fungsi Mencari Elemen
bool search(Node* root, int key) {
    if (root == NULL) return false;
    if (root->data == key) return true;

    if (key < root->data)
        return search(root->left, key);
    else
        return search(root->right, key);
}

// Fungsi Menghapus Elemen
Node* findMin(Node* root) {
    while (root->left != NULL)
        root = root->left;
    return root;
}

Node* deleteNode(Node* root, int key) {
    if (root == NULL) return NULL;

    if (key < root->data)
        root->left = deleteNode(root->left, key);
    else if (key > root->data)
        root->right = deleteNode(root->right, key);
    else {
        // Kasus 1: Tidak punya anak
        if (root->left == NULL && root->right == NULL)
            return NULL;

        // Kasus 2: Punya satu anak
        if (root->left == NULL) return root->right;
        if (root->right == NULL) return root->left;

        // Kasus 3: Punya dua anak
        Node* temp = findMin(root->right);
        root->data = temp->data;
        root->right = deleteNode(root->right, temp->data);
    }
    return root;
}

// Fungsi Traversal (Inorder)
void inorder(Node* root) {
    if (root == NULL) return;
    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}

int main() {
    Node* root = NULL;
    root = insert(root, 50);
    insert(root, 30);
    insert(root, 70);
    insert(root, 20);
    insert(root, 40);
    insert(root, 60);
    insert(root, 80);

    cout << "Inorder: ";
    inorder(root);
    cout << endl;

    cout << "Search 40: " << (search(root, 40) ? "Found" : "Not Found") << endl;
    
    return 0;
}