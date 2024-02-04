---
title: "[C++ / Algorithm] DFS 탐색 #11"
date: 2024-01-31 23:16:00 +/-TTTT
categories: [algorithm, cpp]
tags: [algorithm, cpp]   # TAG names should always be lowercase
---

## 1. DFS 탐색이란?

**`DFS 탐색`**은 그래프의 탐색 방식 중 하나로 **`깊이 우선 탐색`**이라고도 불립니다.<br>
이름에서 알 수 있듯이 깊이를 우선으로 탐색하는 탐색 방법입니다.<br>
그래프는 노드에서 다음 노드로 넘어갈 때 분기가 생기곤 합니다.<br>
**`깊이 우선 탐색`**은 다음 분기로 넘어가지 않고 해당 분기를 완전히 탐색한 후에 넘어간다는 특징이 있습니다.

## 2. DFS 탐색의 특징

* 자기 자신을 다시 호출하는 순환 알고리즘의 형태를 가지고 있습니다.
* 방문한 노드를 방문하지 않도록 하는 로직을 구현하지 않으면 무한 루트에 빠질 위험이 있습니다.
* 노드를 거꾸로 거쳐 간다는 특징이 있습니다.

## 3. DFS 써보기

아래 코드는 3 * 3의 보드를 DFS로 탐색하는 코드입니다.

```cpp
#include <iostream>
#include <stack>
#include <array>

using namespace std;

array<array<int, 3>, 3> map;
array<array<bool, 3>, 3> visited;

int main() {
    stack<array<int, 2>> bfs;

    bfs.push({ 0, 0 });

    while (!bfs.empty()) {
        array<int, 2> current = bfs.top();
        bfs.pop();

        if (current[0] < 0 || current[0] >= 3 || current[1] < 0 || current[1] >= 3) continue;
        if (visited[current[1]][current[0]]) continue;

        visited[current[1]][current[0]] = true;

        cout << current[1] * 3 + current[0] + 1 << endl;

        bfs.push({ current[0], current[1] - 1 });
        bfs.push({ current[0] - 1, current[1] });
        bfs.push({ current[0], current[1] + 1 });
        bfs.push({ current[0] + 1, current[1] });
    }
}
```
{: file="main.cpp" }
```
1
2
3
6
9
8
7
4
5

```
{: file="output.txt" }