---
title: Binary Tree
date: 22-03-2025 12:46
tags:
  - Data-Structure
  - Tree
  - "#Binary-Tree"
---
# Binary Tree

## Deskripsi Singkat  
- **Binary Tree** adalah struktur data hierarkis di mana **setiap simpul (node) memiliki maksimal dua anak** (left child & right child).
- Digunakan dalam banyak aplikasi, seperti **Binary Search Tree (BST), Heap, Huffman Encoding, dan Decision Tree**.

---

## Jenis - Jenis Binary Tree
1. **Full Binary Tree** → Setiap simpul **memiliki 0 atau 2 anak**.
2. **Complete Binary Tree** → Semua level **terisi penuh kecuali level terakhir**.
3. **Perfect Binary Tree** → Semua level **terisi penuh** dan semua simpul memiliki **2 anak**.
4. **Balanced Binary Tree** → Selisih tinggi **subtree kiri dan kanan tidak lebih dari 1**.
5. **Degenerate Tree (Skewed Tree)** → Semua simpul **hanya memiliki satu anak**.

---

## Traversal (Penelusuran)
- Terdapat tiga cara utama untuk menelusuri pohon:
	1. Inorder (Left, Root, RIght).
	2. Preorder (Root, Left, Right).
	3. Postorder (Left, Right, Root).

---

## Source Code
```cpp
#include <iostream>

using namespace std;

struct Node {
	int data;
	Node* left;
	Node* right;

	// Constructor
	Node(int val) {
		data = val;
		left = right = nullptr;
	}
}

void preorder(Node* root) {
	if (root == nullptr) return;
	cout << root->data << " ";
	preorder(root->left);
	preorder(root->right);
}

void inorder(Node* root) {
	if (root == nullptr) return;
	inorder(root->left);
	cout << root->data << " ";
	inorder(root->right);
}

void postorder(Node* root) {
	if (root == nullptr) return;
	postorder(root->left);
	postorder(root->right);
	cout << root->data << " ";
}

int main() {
	Node *root = new Node(1);
	root->left = new Node(2);
	root->right = new Node(3);
	root->left->left = new Node(4);
	root->left->right = new Node(5);
	root->right->right = new Node(6);

	cout << "Preorder: ";
	preorder(root);
	cout << endl;
	cout << "Inorder: ";
	inorder(root);
	cout << endl;
	cout << "Postorder: "; 
	postorder(root);
	cout << endl;

	return 0;
}