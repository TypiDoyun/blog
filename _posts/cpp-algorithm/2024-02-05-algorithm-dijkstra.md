---
title: "[C++ / Algorithm] Dijkstra 길찾기 #14"
date: 2024-02-05 22:016:00 +/-TTTT
categories: [algorithm, cpp]
tags: [algorithm, cpp]   # TAG names should always be lowercase
---

## 1. 다익스트라 알고리즘의 특징

다익스트라 알고리즘은 그래프에서 두 노드 사이의 최단 거리를 찾는 알고리즘으로,<br>
노드 사이를 잇는 간선이 가중치를 가집니다.

## 2. 다익스트라 알고리즘 설명

다익스트라는 모든 노드를 방문해서 그 노드까지 이동하는데 필요한 최소 거리를 계속 갱신하는 방식으로 작동합니다.

## 3. 최단 거리 출력 코드

```cpp
#include <iostream>
#include <array>
#include <queue>

using namespace std;

struct Position {
    int x;
    int y;
};

typedef array<array<int, 5>, 5> Map;

Map map = { {
    { 0, 1, 0, 0, 0 },
    { 0, 1, 0, 1, 0 },
    { 0, 1, 0, 0, 0 },
    { 0, 1, 0, 1, 0 },
    { 0, 0, 0, 1, 0 }
} };

Map dist = { {
    { 0, -1, -1, -1, -1 },
    { -1, -1, -1, -1, -1 },
    { -1, -1, -1, -1, -1 },
    { -1, -1, -1, -1, -1 },
    { -1, -1, -1, -1, -1 }
} };

void setDistance(Position position, int current) {
    if (position.x < 0 || position.y < 0) return;
    if (position.x >= 5 || position.y >= 5) return;
    if (map[position.y][position.x]) return;

    int& d = dist[position.y][position.x];
    
    if (d == -1) d = current + 1;
    else if (d > current + 1) d = current + 1;
}

void dijkstra(Position from, Position to) {
    queue<Position> positions;

    positions.push(from);

    while (!positions.empty()) {
        Position current = positions.front();
        positions.pop();

        if (current.x < 0 || current.y < 0) continue;
        if (current.x >= 5 || current.y >= 5) continue;
        if (map[current.y][current.x]) continue;

        map[current.y][current.x] = 2;

        setDistance({ current.x + 1, current.y }, dist[current.y][current.x]);
        setDistance({ current.x - 1, current.y }, dist[current.y][current.x]);
        setDistance({ current.x, current.y + 1 }, dist[current.y][current.x]);
        setDistance({ current.x, current.y - 1 }, dist[current.y][current.x]);

        positions.push({ current.x + 1, current.y });
        positions.push({ current.x - 1, current.y });
        positions.push({ current.x, current.y + 1 });
        positions.push({ current.x, current.y - 1 });
    }
}

int main() {
    dijkstra({ 0, 0 }, { 4, 4 });
    
    for (auto line : dist) {
        for (int land : line) {
            cout << land << " ";
        }
        cout << endl;
    }

    return 0;
}
```
{: file="main.cpp" }
```
0 -1 10 11 12 
1 -1 9 -1 11 
2 -1 8 9 10 
3 -1 7 -1 11 
4 5 6 -1 12

```
{: file="output.txt" }