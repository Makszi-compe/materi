---
title: Algoritma dan Strukutr Data pada Bahasa dan Otomata
date: 23-03-2025 02:10
tags:
  - Algorithm
  - Competitive-Programming
  - "#Parsing"
  - "#Stack"
  - "#Tree"
  - "#String-Matching"
  - "#KMP"
  - "#Regex"
  - CPP
---
# Algoritma dan Strukutr Data pada Bahasa dan Otomata

## Deskripsi Singkat  
- **Bahasa dan Otomata** adalah bidang dalam ilmu komputer yang mempelajari **bagaimana mesin memahami, mengenali, dan memproses bahasa formal**.
- **Bahasa Formal** → Kumpulan string yang dihasilkan berdasarkan aturan tertentu.
- **Otomata (Automata)** → Model matematika yang digunakan untuk memproses bahasa formal.

---

## Struktur Data dalam Bahasa dan Otomata
### Graph & Automata
- **Finite State Automaton (FSA)** → Model berbasis **Graph** untuk memproses string.
- Digunakan dalam: **Regular Expression Matching, Kompiler & Analisis Sintaksis.**
- Graph digunakan untuk merepresentasikan transisi antar state.
- Contoh Finite State Automaton (DFA) untuk mendeteksi "abc": 
```scss
Start → (a) → (b) → (c) → Accept
```
### Stack dalam Pushdown Automata (PDA)
- **Pushdown Automata (PDA)** digunakan untuk memproses **Bahasa Bebas-Konteks (Context-Free Language)**.
- Digunakan dalam: **Parsing ekspresi matematika** (`(a + b) * c`) dan **Validasi tanda kurung (Balanced Parentheses)**
-  Contoh Implementasi Validasi Tanda Kurung dengan Stack di C++:
```cpp
#include <iostream>
#include <stack>

using namespace std;

bool isValid(string s) {
    stack<char> st;
    for (char c : s) {
        if (c == '(') st.push(c);
        else {
            if (st.empty()) return false;
            st.pop();
        }
    }
    return st.empty();
}

int main() {
    cout << isValid("((()))") << endl; // Output: 1 (true)
    cout << isValid("(()") << endl;    // Output: 0 (false)
    
    return 0;
}
```
### Tree dalam Parsing dan Compiler
- **Parse Tree** digunakan dalam **Sintaksis Bahasa Pemrograman**.
- Digunakan dalam: **Parsing ekspresi matematika (`(3 + 5) * 2`)** dan **untuk menganalisis kode sumber**.
- Contoh Parse Tree untuk `(3 + 5) * 2`:
```markdown
        (*)
       /   \
     (+)    2
    /   \
   3     5
```

---

## Algoritma dalam Bahasa dan Otomata
### String Matching dengan Finite Automaton
- Gunakan Finite State Automaton (FSA) untuk pencocokan pola dalam string.
- Konsep ini digunakan dalam KMP dan Regex Matching.
```cpp
#include <iostream>

using namespace std;

bool finiteAutomaton(string text, string pattern) {
    int n = text.size(), m = pattern.size();
    for (int i = 0; i <= n - m; i++) {
        if (text.substr(i, m) == pattern) return true;
    }
    return false;
}

int main() {
    cout << finiteAutomaton("xabcyabc", "abc") << endl; // Output: 1 (true)
    
    return 0;
}
```
### Knuth-Morris-Pratt (KMP) untuk String Matching
- Gunakan Prefix Function untuk pencarian pola yang efisien (`O(n + m)`).
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
    KMPSearch("xabcyabc", "abc");
    
    return 0;
}
```
### Automata pada Regular Expression (Regex Matching)
- Gunakan Regex Engine untuk mencocokkan pola dalam teks.
```cpp
#include <iostream>
#include <regex>

using namespace std;

int main() {
    string text = "Email saya adalah example@mail.com";
    regex pattern(R"([a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,})");

    if (regex_search(text, pattern)) {
        cout << "Email ditemukan!" << endl;
    } else {
        cout << "Email tidak ditemukan!" << endl;
    }

    return 0;
}
```

---

## Waktu Penggunaan
- **Gunakan Graph jika**: Menangani transisi antar state dalam Automata.
- **Gunakan Stack jika**: Menangani parsing ekspresi seperti `((a+b)*c)`.
- **Gunakan Tree jika**: Membuat Parser atau Compiler.
- **Gunakan KMP jika**: Mencari pola dalam teks yang panjang.
- **Gunakan Regex jika**: Validasi input seperti email dan nomor telepon.

---
