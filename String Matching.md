---
title: String Matching
date: 23-03-2025 01:54
tags:
  - Competitive-Programming
  - "#String-Matching"
  - Algorithm
  - Data-Structure
  - "#Pattern-Matching"
  - "#KMP"
  - "#Rabin-Karp"
  - "#Boyer-Moore"
  - "#CPP"
---
# String Matching

## Deskripsi Singkat  
- **String Matching** adalah teknik untuk **mencari pola (pattern) dalam sebuah teks (string utama)**.
- **Sederhananya**, jika kita memiliki teks `T = "abracadabra"` dan pola `P = "abra"`, maka kita ingin menemukan **semua kemunculan "abra" dalam "abracadabra"**.

---

## Jenis - Jenis Algoritma String Matching
### Brute Force
- Cek setiap posisi dalam teks dan lihat apakah pola cocok.
- **Kompleksitas Waktu:** **O(n × m)**
- **Kekurangan:** **Lambat untuk teks besar**.
```cpp
#include <iostream>

using namespace std;

void bruteForceSearch(string text, string pattern) {
    int n = text.size(), m = pattern.size();
    
    for (int i = 0; i <= n - m; i++) {
        int j;
        for (j = 0; j < m; j++) {
            if (text[i + j] != pattern[j]) break;
        }
        if (j == m) cout << "Pattern ditemukan di indeks " << i << endl;
    }
}

int main() {
    string text = "abracadabra";
    string pattern = "abra";
    bruteForceSearch(text, pattern);
    
    return 0;
}
```
### Knuth-Morris-Pratt (KMP) Algorithm
- Gunakan **prefix function (LPS - Longest Prefix Suffix)** untuk **menghindari perulangan karakter yang tidak perlu**.
- **Kompleksitas Waktu:** **O(n + m)**
- **Kelebihan:** **Lebih cepat dibanding Brute Force!**
- **Kekurangan:** **Lebih sulit dipahami dibanding metode lain.**
```cpp
#include <iostream>
#include <vector>

using namespace std;

vector<int> computeLPS(string pattern) {
    int m = pattern.size(), j = 0;
    vector<int> lps(m, 0);
    
    for (int i = 1; i < m; i++) {
        while (j > 0 && pattern[i] != pattern[j]) j = lps[j - 1];
        if (pattern[i] == pattern[j]) j++;
        lps[i] = j;
    }
    return lps;
}

void KMPSearch(string text, string pattern) {
    int n = text.size(), m = pattern.size(), j = 0;
    vector<int> lps = computeLPS(pattern);

    for (int i = 0; i < n; i++) {
        while (j > 0 && text[i] != pattern[j]) j = lps[j - 1];
        if (text[i] == pattern[j]) j++;
        if (j == m) {
            cout << "Pattern ditemukan di indeks " << i - m + 1 << endl;
            j = lps[j - 1];
        }
    }
}

int main() {
    string text = "abracadabra";
    string pattern = "abra";
    KMPSearch(text, pattern);
    
    return 0;
}
```
### Rabin-Karp-Algorithm
- Gunakan **hashing** untuk membandingkan pola dengan substring dalam teks
- **Kompleksitas Waktu:** **O(n + m) rata-rata**
- **Kelebihan:** **Cocok untuk mencari banyak pola sekaligus.**
- **Kekurangan:** **Bisa menjadi O(nm) dalam worst case.**
```cpp
#include <iostream>

using namespace std;

const int d = 256;
const int q = 101; // Bilangan prima untuk modulus hashing

void rabinKarp(string text, string pattern) {
    int n = text.size(), m = pattern.size();
    int h = 1, pHash = 0, tHash = 0;

    for (int i = 0; i < m - 1; i++) h = (h * d) % q;
    for (int i = 0; i < m; i++) {
        pHash = (d * pHash + pattern[i]) % q;
        tHash = (d * tHash + text[i]) % q;
    }

    for (int i = 0; i <= n - m; i++) {
        if (pHash == tHash) {
            bool match = true;
            for (int j = 0; j < m; j++) {
                if (text[i + j] != pattern[j]) {
                    match = false;
                    break;
                }
            }
            if (match) cout << "Pattern ditemukan di indeks " << i << endl;
        }
        if (i < n - m) {
            tHash = (d * (tHash - text[i] * h) + text[i + m]) % q;
            if (tHash < 0) tHash += q;
        }
    }
}

int main() {
    string text = "abracadabra";
    string pattern = "abra";
    rabinKarp(text, pattern);
    
    return 0;
}
```
### Boyer-Moore Algorithm
- **Melakukan pencarian mundur** pada pola dan menggunakan **heuristik shifting** untuk mempercepat pencocokan.
```cpp
#include <bits/stdc++.h>

using namespace std;

#define NO_OF_CHARS 256

// The preprocessing function for Boyer Moore's
// bad character heuristic
void badCharHeuristic(string str, int size,
					int badchar[NO_OF_CHARS])
{
	int i;

	// Initialize all occurrences as -1
	for (i = 0; i < NO_OF_CHARS; i++)
		badchar[i] = -1;

	// Fill the actual value of last occurrence
	// of a character
	for (i = 0; i < size; i++)
		badchar[(int)str[i]] = i;
}

void search(string txt, string pat)
{
	int m = pat.size();
	int n = txt.size();
	int badchar[NO_OF_CHARS];
	
	badCharHeuristic(pat, m, badchar);

	int s = 0; // s is shift of the pattern with
			// respect to text
	while (s <= (n - m)) {
		int j = m - 1;

		while (j >= 0 && pat[j] == txt[s + j])
			j--;

		if (j < 0) {
			cout << "pattern occurs at shift = " << s
				<< endl;
				
			s += (s + m < n) ? m - badchar[txt[s + m]] : 1;
		}

		else
			s += max(1, j - badchar[txt[s + j]]);
	}
}

int main()
{
	string txt = "ABAAABCD";
	string pat = "ABC";
	search(txt, pat);
	
	return 0;
}
```

---

## Waktu Penggunaan
- **Gunakan Brute Force jika**: Teks pendek dan pencarian dilakukan sekali saja.
- **Gunakan KMP jika**: Pencarian dilakukan **berulang kali** pada teks panjang.
- **Gunakan Rabin-Karp jika**: Butuh pencarian **banyak pola sekaligus**.
- **Gunakan Boyer-Moore jika**: Teks **sangat panjang** dan perlu pencarian cepat.
## Source Code
```cpp
#include <header_file>