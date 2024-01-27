---
title: "[C++ / Algorithm] 큐 #6"
date: 2024-01-27 22:25:00 +/-TTTT
categories: [algorithm, cpp]
tags: [algorithm, cpp]   # TAG names should always be lowercase
---

## 1. 큐란?

큐는 선형 자료구조로 먼저 들어온 데이터가 먼저 처리된다는 특징이 있습니다.<br>
큐는 일상 생활에 비교한다면 줄서기와 비슷하다고 할 수 있습니다.

----

## 2. C++에서의 큐

C++에서는 큐를 **정규 라이브러리에서 지원**하고 있습니다.

```cpp
#include <iostream>
#include <queue>

using namespace std;

int main() {
    queue<int> myQueue;

    myQueue.push(1);
    myQueue.push(2);
    myQueue.push(3);

    cout << myQueue.back() << " ";
    myQueue.pop();
    cout << myQueue.back() << " ";
    myQueue.pop();
    cout << myQueue.back() << " ";
    myQueue.pop();

    return 0;
}
```
{: file="main.cpp" }
```
1 2 3 
```
{: file="output.txt" }

일반적인 사용법은 스택과 동일하지만 다음 요소를 얻는 메소드가 **`back`**으로 변경되었습니다.
큐는 **`선입선출`**의 특징을 가져 알고리즘 문제 풀이에 다양하게 활용됩니다.