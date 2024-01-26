---
title: "[C++ / Algorithm] 연결 리스트 #5"
date: 2024-01-25 23:30:00 +/-TTTT
categories: [algorithm, cpp]
tags: [algorithm, cpp]   # TAG names should always be lowercase
---

## 1. 연결 리스트란?

연결 리스트는 각각의 데이터가 메모리에 비 연속적으로 저장되는 자료 구조입니다.<br>
연결 리스트 또한 순서를 가지는 선형 자료구조이므로 각각의 데이터는 다음 요소의 메모리 주소를 저장합니다.

----

## 2. 연결 리스트의 노드

연결 리스트는 각각의 데이터를 노드에 저장합니다.<br>
노드는 데이터 영역과 포인터 영역을 가지며 포인터 영역은 다음 노드의 주소를 가르킵니다.

----

## 3. C++에서의 연결 리스트

C++에서는 보통 아래와 같이 연결 리스트를 사용합니다.

```cpp
#include <iostream>
#include <list>

using namespace std;

int main() {
    list<int> linkedList = { 1, 5, 7, 3, 2, 8, 6 };

    linkedList.push_back(4);
    linkedList.push_front(9);

    for (int item : linkedList) {
        cout << item << " ";
    }

    return 0;
}
```
{: file="main.cpp" }
```
9 1 5 7 3 2 8 6 4 
```
{: file="output.txt" }

연결 리스트는 배열과 다르게 요소를 삽입하는 연산은 시간 복잡도가 **`O(1)`**으로 괴장히 짧습니다.<br>
하지만 N번째 요소를 읽는 연산은 **`O(N)`**의 시간 복잡도가 걸린다는 단점이 있습니다.

## 4. 연결 리스트의 종류

### 4-1. 단순 연결 리스트

단순 연결 리스트는 **노드에 포인터 영역이 1개만 있는 연결 리스트**로 다음 요소만을 가르켜 이전 요소로 돌아갈 수 없다는 특징이 있습니다.

----

### 4-2. 이중 연결 리스트

이중 연결 리스트는 **노드에 포인터 영역이 2개가 존재하는 연결 리스트**로 다음 요소와 이전 요소를 모두 가르켜 이동에 제약이 없다는 특징이 있습니다.