---
title: Teori Graf
date: 23-03-2025 12:36
tags:
  - Graph
  - Algorithm
  - Data-Structure
  - Competitive-Programming
  - DFS
  - "#BFS"
  - "#Dijkstra"
---
# Teori Graf

## Deskripsi Singkat  
- **Teori Graf** adalah cabang ilmu komputer dan matematika yang mempelajari **struktur jaringan hubungan antar objek**.
- Graf terdiri dari:
	- **Simpul (Vertex, Node)** → Titik yang mewakili objek.
	- **Sisi (Edge)** → Garis yang menghubungkan dua simpul.

---

## Jenis - Jenis Graf
- Berdasarkan Jenis Sisi (Edge)
	- **Graf Tak Berarah (Undirected Graph)** → Sisi tidak memiliki arah.
	- **Graf Berarah (Directed Graph, DAG)** → Sisi memiliki arah tertentu.
- Berdasarkan Bobot (Weight)
	- **Graf Berbobot (Weighted Graph)** → Sisi memiliki nilai (jarak, biaya, dll.).
	- **Graf Tak Berbobot (Unweighted Graph)** → Semua sisi dianggap memiliki bobot yang sama.
- Berdasarkan Hubungan Antar Simpul
	- **Graf Terhubung (Connected Graph)** → Semua simpul saling terhubung.
	- **Graf Tidak Terhubung (Disconnected Graph)** → Ada simpul yang tidak memiliki jalur ke simpul lain.

---

## Representasi Graf dalam Competitive Programming
### Adjacency Matrix (Matriks Ketetanggaan)
- Gunakan array 2D `adj[n][n]` untuk menyimpan hubungan antar simpul.
- **Kelebihan:** Akses cepat `O(1)`.
- **Kekurangan:** Boros memori untuk graf jarang (sparse graph).
- Contoh:
```less
   A --- B
   |     |
   C --- D
```
- Representasi Adjacency Matrix:
```css
  A B C D
A 0 1 1 0
B 1 0 0 1
C 1 0 0 1
D 0 1 1 0
```
- Implementasi di C++:
```cpp
#include <iostream>

using namespace std;

int adj[4][4] = {
    {0, 1, 1, 0},
    {1, 0, 0, 1},
    {1, 0, 0, 1},
    {0, 1, 1, 0}
};

int main() {
    cout << "Apakah A terhubung dengan B? " << adj[0][1] << endl;
    
    return 0;
}
```
### Adjacency List (List Ketetanggaan)
- Gunakan `vector<int> adj[n]` untuk menyimpan daftar tetangga setiap simpul.
- **Kelebihan:** Hemat memori untuk graf jarang.
- **Kekurangan:** Akses ke elemen tertentu lebih lambat daripada matriks.
- Implementasi di C++:
```cpp
#include <iostream>
#include <vector>

using namespace std;

vector<int> adj[4];

int main() {
    adj[0] = {1, 2}; // A -> B, C
    adj[1] = {0, 3}; // B -> A, D
    adj[2] = {0, 3}; // C -> A, D
    adj[3] = {1, 2}; // D -> B, C

    cout << "Tetangga A: ";
    for (int neighbor : adj[0]) cout << neighbor << " ";
    
    return 0;
}
```

---

## Algoritma Penting dalam Teori Graf
### Depth-First-Search (DFS)
- **Digunakan untuk:** Mengecek keterhubungan antar simpul dan Menelusuri seluruh jalur dalam graf.
- **Kompleksitas Waktu:** **O(V + E)**.
- Implementasi DFS di C++ (Rekursif)
```cpp
#include <iostream>
#include <vector>

using namespace std;

vector<int> adj[100];
bool visited[100];

void dfs(int node) {
    visited[node] = true;
    cout << node << " ";
    for (int neighbor : adj[node]) {
        if (!visited[neighbor]) dfs(neighbor);
    }
}

int main() {
    adj[0] = {1, 2};
    adj[1] = {0, 3};
    adj[2] = {0, 3};
    adj[3] = {1, 2};

    dfs(0); // Output: 0 1 3 2 (bisa berbeda tergantung urutan list)
    
    return 0;
}
```
### Breadth-First-Search (BFS)
- Digunakan untuk: Menemukan jalur terpendek dalam graf tak berbobot dan Mencari konektivitas antar simpul.
- **Kompleksitas Waktu:** **O(V + E)**.
- Implementasi BFS di C++ (Menggunakan Queue)
```cpp
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

vector<int> adj[100];
bool visited[100];

void bfs(int start) {
    queue<int> q;
    q.push(start);
    visited[start] = true;

    while (!q.empty()) {
        int node = q.front();
        q.pop();
        cout << node << " ";
        for (int neighbor : adj[node]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}

int main() {
    adj[0] = {1, 2};
    adj[1] = {0, 3};
    adj[2] = {0, 3};
    adj[3] = {1, 2};

    bfs(0); // Output: 0 1 2 3
    
    return 0;
}
```
### Dijkstra’s Algorithm (Jalur Terpendek di Graf Berbobot)
- Digunakan untuk: Menemukan jalur terpendek dari satu simpul ke semua simpul lainnya.
- **Kompleksitas Waktu:** **O((V + E) log V)**.
- Implementasi Dijkstra di C++ (Menggunakan Priority Queue)
```cpp
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

const int INF = 1e9;
vector<pair<int, int>> adj[100];

void dijkstra(int start, int V) {
    vector<int> dist(V, INF);
    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<>> pq;

    dist[start] = 0;
    pq.push({0, start});

    while (!pq.empty()) {
        int d = pq.top().first;
        int node = pq.top().second;
        pq.pop();

        if (d > dist[node]) continue;

        for (auto edge : adj[node]) {
            int weight = edge.first;
            int neighbor = edge.second;

            if (dist[node] + weight < dist[neighbor]) {
                dist[neighbor] = dist[node] + weight;
                pq.push({dist[neighbor], neighbor});
            }
        }
    }

    for (int i = 0; i < V; i++)
        cout << "Jarak ke " << i << ": " << dist[i] << endl;
}

int main() {
    adj[0].push_back({4, 1});
    adj[0].push_back({1, 2});
    adj[1].push_back({2, 2});
    adj[2].push_back({3, 3});

    dijkstra(0, 4);
    
    return 0;
}
```