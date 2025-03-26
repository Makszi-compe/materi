---
title: Algoritma dan Struktur Data pada Natural Language Processing (NLP)
date: 23-03-2025 12:18
tags:
  - "#Natural-Language-Processing"
  - Algorithm
  - Data-Structure
  - Competitive-Programming
  - "#Trie"
  - "#Hash-Table"
  - "#Graph"
  - "#Matrix"
  - "#Machine-Learning"
  - "#Text-Processing"
  - "#CPP"
---
# Algoritma dan Struktur Data pada Natural Language Processing (NLP)

## Deskripsi Singkat  
- **Natural Language Processing (NLP)** adalah cabang kecerdasan buatan (AI) yang memungkinkan komputer memahami, menganalisis, dan memproses bahasa manusia.

---

## Struktur Data dalam NLP

| Struktur Data                   | Digunakan Dalam                              |
| ------------------------------- | -------------------------------------------- |
| Trie (Prefix Tree)              | Aucomplete, Spell Checker.                   |
| Hash Table (Dictionary)         | Penyimpanan frekuensi kata.                  |
| Graph                           | Representasi hubungan antar kata dalam teks. |
| Heap & Priority Queue           | Menentukan kata paling sering muncul.        |
| Matrix (TF-IDF, Word Embedding) | Representasi kata dalam bentuk vektor.       |

---

## Algoritma dalam NLP
### Trie untuk Autocomplete dan Spell Checker
- Trie adalah struktur data yang cocok untuk pencarian cepat dalam kamus kata.
- Trie sangat cepat dalam pencarian kata (`O(m)`, dengan `m` panjang kata).
- Implementasi Trie di C++
```cpp
#include <iostream>
#include <unordered_map>

using namespace std;

struct TrieNode {
    unordered_map<char, TrieNode*> children;
    bool isEnd = false;
};

class Trie {
public:
    TrieNode* root;
    Trie() { root = new TrieNode(); }

    void insert(string word) {
        TrieNode* node = root;
        for (char c : word) {
            if (!node->children.count(c)) node->children[c] = new TrieNode();
            node = node->children[c];
        }
        node->isEnd = true;
    }

    bool search(string word) {
        TrieNode* node = root;
        for (char c : word) {
            if (!node->children.count(c)) return false;
            node = node->children[c];
        }
        return node->isEnd;
    }
};

int main() {
    Trie trie;
    trie.insert("hello");
    cout << trie.search("hello") << endl; // Output: 1 (true)
    cout << trie.search("world") << endl; // Output: 0 (false)
    
    return 0;
}
```
### Hash Table untuk Perhitungan Frekuensi Kata (Word Count)
- Hash Table (`unordered_map`) digunakan untuk menghitung jumlah kemunculan kata dalam teks.
- Hash Table (`unordered_map`) memiliki waktu pencarian rata-rata `O(1)`.
- Implementasi Word Count di C++
```cpp
#include <iostream>
#include <unordered_map>
#include <sstream>

using namespace std;

int main() {
    string text = "the quick brown fox jumps over the lazy dog";
    unordered_map<string, int> freq;
    stringstream ss(text);
    string word;

    while (ss >> word) freq[word]++;

    for (auto p : freq) cout << p.first << " : " << p.second << endl;

    return 0;
}
```
### Graph untuk Analisis Hubungan Antar Kata (Text Graph Analysis)
- Graph digunakan untuk menemukan hubungan antar kata dalam teks, misalnya dalam Google PageRank atau Knowledge Graph.
- Contoh Representasi Graph dari Kalimat:
```mathematica
"The cat eats fish" → Graph:
  "The" → "cat"
  "cat" → "eats"
  "eats" → "fish"
```
### TF-IDF untuk Menentukan Kata Penting dalam Dokumen
- **TF-IDF (Term Frequency - Inverse Document Frequency)** digunakan dalam **Google Search & NLP** untuk menentukan kata yang paling penting dalam suatu dokumen.
- Formula TF-IDF:
```mathematica
TF-IDF = (Frekuensi kata dalam dokumen) × log(Total dokumen / Dokumen yang mengandung kata)
```
### N-grams untuk Model Prediksi Teks
- N-grams adalah teknik NLP yang menggunakan urutan kata untuk memprediksi teks selanjutnya.
- Digunakan dalam Autocomplete, Speech Recognition, dan Machine Translation.
- Contoh N-grams (`N = 2` / Bigram):
```vbnet
Teks: "the quick brown fox"
Bigrams: ("the quick"), ("quick brown"), ("brown fox")
```
- Implementasi Bigram di C++
```cpp
#include <iostream>
#include <vector>

using namespace std;

void generateBigrams(vector<string> words) {
    for (size_t i = 0; i < words.size() - 1; i++) {
        cout << "(" << words[i] << ", " << words[i + 1] << ")" << endl;
    }
}

int main() {
    vector<string> words = {"the", "quick", "brown", "fox"};
    generateBigrams(words);
    
    return 0;
}
```

---

## Waktu Penggunaan
- **Gunakan Trie jika**: Butuh pencarian kata cepat dalam kamus atau autocomplete.
- **Gunakan Hash Table jika**: Butuh menghitung frekuensi kata dalam teks.
- **Gunakan Graph jika**: Menganalisis hubungan antar kata dalam teks.
- **Gunakan TF-IDF jika**: Butuh menentukan kata paling penting dalam dokumen.
- **Gunakan N-grams jika**: Butuh memprediksi kata selanjutnya dalam sebuah teks.

---
